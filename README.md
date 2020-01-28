# パターン認識によるデータ分析
このリポジトリにはパターン認識を用いたデータ分析の手法の実装があります．  
トピックは最小2乗回帰と分類，転移学習や半教師あり学習，次元削減などです．  

## 実行
各jupyter notebookは独立した手法でありセルを実行することで試すことができます．  
```
**requirements**
numpy
matplotlib
scipy
mpl_toolkits
pandas
seaborn
sklearn
```

## 各ファイルの概要  

### lsr
最小二乗回帰(Least Squares Regression)  
ガウスカーネルモデルに対してL2正則化を用いた最小二乗回帰を行う．  
コードでは交差確認法によって正則化パラメータとガウス幅を決定している．  

### lsm_admm
交互方向乗数法によるL1スパース回帰(Least Squares Method with Alternating Direction Method of Multipliers)  

### robust_regression
ロバスト回帰  
外れ値があるようなデータに直線モデルを適応させる．  
繰り返し最小二乗アルゴリズムを使ったフーバー回帰(huber regression)，テューキー回帰(tukey regression)を実装．  

### lsc
最小二乗分類(Least Squares Classification)  
ガウスカーネルに対する最小二乗回帰を応用した多クラス分類．  
2クラス分類を複数回繰り返して多クラス分類を実現する．  
1対他法と1対1法がある．  
./digit 以下の数字データファイルを読み込む．  

### svm
サポートベクトルマシン(Support Vector Machine)  
劣勾配アルゴリズムを使った線形モデルに対するサポートベクトルマシン  

### lspc
最小二乗確率的分類(Least Squares Probabilistic Classification)  
ガウスカーネルモデルに対して，最小二乗確率的分類の手法で多クラス分類を行う．  
二乗誤差の最小化を標本近似によって行う．  

### arow
適応正則化分類(Adaptive Regularization Of Weight vectors)  
学習データが1つずつ入ってくるオンライン学習での分類問題．  
パラメータの平均μ，分散Σを更新することで適応的にパラメータを更新していく．  

### lrls
ラプラス正則化最小二乗分類(Laplacian Regularized Least Square classification)  
データのうちラベル付けされたものが半教師付き学習の設定．  
データ空間で近傍にある点同士の出力が滑らかになるような制約式を加えることで，ラベルなしデータを活用する．  

### cwls
クラス比重み付き最小二乗法(Class Weighted Least Squares method)  
訓練データとテストデータでクラスごとのデータ割合が異なるような場合の転移学習の設定．  
クラスごとの分布間距離を近似的に求め，求まったクラス比で線形モデルを重み付けする．  

### lpp
局所性保存射影(Locality Preserving Projection)  
データ集合に対し類似度行列を定義し，局所性保存射影を求めることで，教師なしの次元削減を行う．  
クラスタ構造を保持したまま分散が大きくなるような射影軸を求める．  

### fda
フィッシャー判別分析(Fisher Discriminant Analysis)  
教師ありでクラスタを持つデータに対してフィッシャー判別分析を適用し，クラスカテゴリを考慮した射影直線を求める．  
クラス間分散を最大に，クラス内分散を最小にするように一般固有値問題を解く．  

### lap_eig
ラプラス固有写像(Laplacian Eigen map)  
教師なしで非線形の次元削減をラプラス固有写像を用いて行う．  
類似度行列の生成には最近傍類似度を用いる．  
