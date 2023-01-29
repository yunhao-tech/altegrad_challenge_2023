# [ALTeGrad Challenge 2022-2023 Cellular Component Ontology](https://kaggle.com/competitions/altegrad-2022)

Kaggle team: 朊（Ruan). Other team members: [alephpi](https://github.com/alephpi), [yangzhang33](https://github.com/yangzhang33).

## data description

### outline:

- 6111 graphs(proteins)
- 1572264 nodes(amino acids)
- 15213222 edges(bonds)

`sequence.txt` 6111 lines: i-th line represents the amino acids sequence of i-th protein.

```
AYIAKQRQISFVKSHFSRQLEERLGLIEVQAPILSRVGDGTQDNLSGAEKAVQVKVKALPDAQFEVVHSLAKWKRQTLGQHDFSAGEGLYTHMKALRPDEDRLSPLHSVYVDQWDWERVMGDGERQFSTLKSTVEAIWAGIKATEAAVSEEFGLAPFLPDQIHFVHSQELLSRYPDLDAKGRERAIAKDLGAVFLVGIGGKLSDGHRHDVRAPDYDDWSTPSELGHAGLNGDILVWNPVLEDAFELSSMGIRVDADTLKHQLALTGDEDRLELEWHQALLRGEMPQTIGGGIGQSRLTMLLLQLPHIGQVQAGVWPAAVRESVPSLL
RTDCYGNVNRIDTTGASCKTAKPEGLSYCGVSASKKIAERDLQAMDRYKTIIKKVGEKLCVEPAVIAGIISRESHAGKVLKNGWGDRGNGFGLMQVDKRSHKPQGTWNGEVHITQGTTILINFIKTIQKKFPSWTKDQQLKGGISAYNAGAGNVRSYARMDIGTTHDDYANDVVARAQYYKQHGY
EKKSINECDLKGKKVLIRVDFNVPVKNGKITNDYRIRSALPTLKKVLTEGGSCVLMSHLGRPKGIPMAQAGKIRSTGGVPGFQQKATLKPVAKRLSELLLRPVTFAPDCLNAADVVSKMSPGDVVLLENVRFYKEEGSKKAKDREAMAKILASYGDVYISDAFGTAHRDSATMTGIPKILGNGAAGYLMEKEISYFAKVLGNPPRPLVAIVGGAKVSDKIQLLDNMLQRIDYLLIGGAMAYTFLKAQGYSIGKSKCEESKLEFARSLLKKAEDRKVQVILPIDHVCHTEFKAVDSPLITEDQNIPEGHMALDIGPKTIEKYVQTIGKCKSAIWNGPMGVFEMVPYSKGTFAIAKAMGRGTHEHGLMSIIGGGDSASAAELSGEAKRMSHVSTGGGASLELLEGKTLPGVTVLDDK
```

`edgelist.txt` 15213222 lines: i-th line is a pair of (s,t) represents for s-th and t-th node forms the i-th (undirected) edge.

```
0,1
0,2
0,3
```

`edge_attributes.txt` 15213222 lines: i-th line stores the i-th edge's attribute.
|distance|distance based?|peptide bond?|knn?|hydrogen bond?|
|:-:|:-:|:-:|:-:|:-:|

```
3.789731,1.000000,1.000000,0.000000,0.000000
5.507777,1.000000,0.000000,0.000000,0.000000
5.029150,1.000000,0.000000,0.000000,0.000000
```

`node_attributes.txt` 1572264 lines: i-th line stores the i-th node's attribute.
|x|y|z|amino acid type $\in \lbrace 0,1\rbrace^{20}$|hydrogen bond acceptor?|hydrogen bond donor?|[EXPASY feature](https://web.expasy.org/protscale/) $\in R^{60}$|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

```
12.364000,38.679001,28.167999,1.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,2.350000,9.870000,7.000000,6.110000,89.000000,4.000000,11.500000,0.000000,8.100000,4.340000,78.000000,0.620000,-0.400000,-0.500000,1.800000,12.970000,0.440000,0.616000,0.610000,0.310000,0.100000,0.300000,5.330000,1.360000,0.390000,0.620000,1.940000,1.150000,-0.300000,2.100000,0.420000,0.350000,5.100000,3.900000,7.300000,0.380000,-0.100000,0.500000,11.200000,6.600000,0.380000,0.740000,0.000000,86.599998,0.360000,1.420000,0.830000,0.660000,1.489000,0.709000,0.788000,0.824000,1.290000,0.900000,0.770000,0.920000,0.900000,1.000000,8.300000,8.250000,100.000000
15.490000,39.455002,26.171000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,1.000000,1.000000,1.000000,2.200000,9.110000,10.070000,5.630000,181.000000,2.000000,18.030001,1.610000,6.200000,31.530001,84.000000,0.260000,1.670000,-2.300000,-1.300000,13.420000,1.630000,0.880000,-1.430000,0.960000,-0.210000,-0.400000,5.890000,0.830000,1.470000,0.260000,-6.110000,0.130000,7.100000,-1.900000,0.510000,0.390000,8.000000,3.800000,5.900000,0.490000,8.200000,6.100000,2.600000,5.100000,0.150000,0.760000,0.200000,177.699997,0.420000,0.690000,1.470000,1.140000,0.787000,1.266000,0.795000,1.109000,0.720000,1.250000,1.050000,1.530000,1.680000,1.080000,3.200000,2.920000,41.000000
17.768000,39.050999,29.165001,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,1.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,0.000000,2.320000,9.760000,7.000000,6.040000,131.000000,3.000000,21.400000,0.130000,5.200000,19.059999,88.000000,1.380000,1.250000,-1.800000,4.500000,15.670000,2.460000,0.943000,-1.450000,1.800000,-1.130000,0.700000,8.830000,1.440000,1.820000,1.380000,2.150000,-2.920000,4.300000,-8.000000,1.810000,1.830000,9.300000,11.000000,6.600000,1.970000,11.800000,13.900000,8.600000,2.800000,0.600000,0.880000,0.000000,158.000000,0.460000,1.080000,1.600000,0.470000,1.003000,1.799000,0.240000,0.886000,0.970000,1.450000,0.510000,1.810000,1.540000,2.600000,5.200000,5.960000,96.000000
```

`graph_indicator.txt` 1572264 lines: i-th line is a value k represents for i-th node $\in$ k-th graph

```
0
0
0
```

`graph_labels.txt` 6111 lines: i-th line represents i-th protein.
|name|class $\in \lbrace \emptyset,0,\cdots,17 \rbrace$|
|:-:|:-:|

```
11as,
154l,8
16pk,
```

### bibliography

webpages:

[一文极速读懂 Gene Ontology （GO）数据库](https://zhuanlan.zhihu.com/p/99789859)
[ICLR'22| 基于知识图谱的蛋白质预训练框架](https://zhuanlan.zhihu.com/p/463331534)

important articles:

- ProteinBERT a universal deep-learning model of protein
- Deep Dive into Machine Learning Models for Protein Engineering

```
bibs
┣ alpha
┃ ┗ Highly accurate protein structure prediction with alphafold.pdf
┣ embedding
┃ ┣ Application of Sequence Embedding in Protein Sequence-Based Predictions.pdf
┃ ┣ OntoProtein Protein Pretraining With Gene Ontology Embedding.pdf
┃ ┗
┣ esm
┃ ┣ Evolutionary-scale prediction of atomic level protein structure.pdf
┃ ┗ Transformer protein language models are unsupervised structure learners.pdf
┗ general
┃ ┣
┃ ┣ Deep Learning for Genomics A Concise Overview.pdf
┃ ┗ Recent Advances in the Prediction of Protein Structural Classe.pdf
```

### 基本思路

基本流程是：特征提取、特征筛选（降维）、分类。特征提取的话分别考虑序列信息和结构信息，序列信息用预训练模型（参见 bib，这个基本不用自己做），结构信息用图神经网络（也可以用简单的图特征提取方法，比如 graph kernel 啥的），提取的特征最后放到分类器里（这个没得说 autogluon 天下无敌）。不过为了更快判断特征提取的优劣，没必要次次调用 autogluon，可以先用最简单的两层 mlp 试试（就接在 gnn 的后面作为一个分类 head）看看和基线区别怎么样，好的话再用 autogluon，这样可以快速排除表现不好的模型。

先考虑单独使用序列信息或结构信息的最好效果

只使用序列信息：目前最好效果是 proteinBert + TruncatedSVM 100 dim + autogluon， 这方面应该到极限了，进步方向就是找更好的预训练模型代替 proteinBert 提取序列 embedding（ESM 不如 proteinBert）
只使用结构信息：目前只使用了节点特征，做消息传递，最后聚合为图特征，效果与基线差别不大。改进方向按顺序：1.考虑更有层次性的聚合方式（求和聚合太扁平，会损失很多信息） 2. 用 soat 的图神经网络（与 1 有部分重合）3.加入边特征

最后可以考虑将两种信息合并训练一个分类器。
