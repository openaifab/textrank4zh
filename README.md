# textrank4zh

TextRank算法可以用來從文本中提取關鍵詞和摘要（重要的句子）。TextRank4ZH是針對中文文本的TextRank算法的python算法實現。

安装方式:

$ pip install textrank4zh

原理
TextRank的詳細原理請參考：

Mihalcea R, Tarau P. TextRank: Bringing order into texts[C]. Association for Computational Linguistics, 2004.

關鍵詞提取
將原文本拆分為句子，在每個句子中過濾掉停用詞（可選），並只保留指定詞性的單詞（可選）。由此可以得到句子的集合和單詞的集合。

每個單詞作為pagerank中的一個節點。設定窗口大小為k，假設一個句子依次由下面的單詞組成：

w1, w2, w3, w4, w5, ..., wn
w1, w2, ..., wk、w2, w3, ...,wk+1、w3, w4, ...,wk+2等都是一個窗口。在一個窗口中的任兩個單詞對應的節點之間存在一個無向無權的邊。

基於上面構成圖，可以計算出每個單詞節點的重要性。最重要的若幹單詞可以作為關鍵詞。

關鍵短語提取
參照關鍵詞提取提取出若幹關鍵詞。若原文本中存在若幹個關鍵詞相鄰的情況，那麽這些關鍵詞可以構成一個關鍵詞組。

例如，在一篇介紹支持向量機的文章中，可以找到關鍵詞支持、向量、機，通過關鍵詞組提取，可以得到支持向量機。

摘要生成
將每個句子看成圖中的一個節點，若兩個句子之間有相似性，認為對應的兩個節點之間有一個無向有權邊，權值是相似度。

通過pagerank算法計算得到的重要性最高的若幹句子可以當作摘要。


此範例(textrank4zh.ipynb)是示範如何用textrank4zh對內容做關鍵詞與關鍵短語還有摘要的使用
步驟如下:
1.用request套件抓取指定網址的內容

2.利用textrank的get_keywords取得關鍵詞

3.利用textrank的get_keyphrases取得關鍵短語

4.利用texkrank的get_key_sentences取得摘要

![image](https://github.com/openaifab/textrank4zh/blob/master/textrank.jpg)
