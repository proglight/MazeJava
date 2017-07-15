# MazeJava

## 概要
様々な迷路の探索を行うJavaアプリケーション。強化学習（Q学習）による探索も実装。

## 開発環境・言語
Eclipse 4.6 (Neon)，Java

## 更新履歴
|ver.|更新日|内容|
|:-|:-|:-|
|1.0|2017/07/10|初版。|
|1.1|2017/07/11|幅優先探索で最短ステップの表示機能を追加。|
|2.0|2017/07/14|強化学習（Q学習）による探索を追加。|
|2.1|2017/07/15|ボタンの不具合を修正。|

## ファイル構成
#### ソースファイル
mazeフォルダ内
- MainMain.java：迷路実行のメインクラス。
- MazeBasic.java：迷路の基本データを読み込むクラス。
- MazeGUI.java：迷路の画面描画処理を行うクラス。
- MazeDepth.java：深さ優先探索を行うクラス。
- MazeBreadth.java：幅優先探索を行うクラス。
- MazeRandom.java：ランダムに探索を行うクラス。

mazeQlearningフォルダ内
- MazeQMain.java：強化学習（Q学習）による迷路探索実行のメインクラス。
- MazeQGUI.java：強化学習による迷路探索描画処理を行うクラス。
- MazeQlearning.java：強化学習による迷路探索を行うクラス。

#### 実行ファイル
- MazeMain.java：迷路の実行ファイル。
- MazeQMain.java：強化学習による迷路探索の実行ファイル。

#### CSVファイル
- InitialMaze.csv：迷路の基本データのサンプルファイル。

## 実行準備
#### 迷路基本データファイルの準備
サンプルファイル以外の迷路データを読み込むことも可能。カンマ区切りのCSVファイルで、0：通路、1：壁、2：スタート、3：ゴールとする。詳細はCSVファイルを参照。なお、ゴールにたどり着けない迷路の場合はエラーが出るので注意。

完成したCSVファイルは、ソースファイルと同じフォルダ内に配置する。
また、**MazeBasic.java**のファイル読み込み部分（inputMazeメソッド内）のパスを各実行環境に合わせて設定しておく。

``` java
//jarで実行の場合
//File f = new File("./initialMaze.csv");
//eclipseで実行の場合
File f = new File("./src/maze/initialMaze.csv");
```

迷路の大きさを変更した場合は、**MazeBasic.java**、**MazeGUI.java**（MazeQMain実行時は**MazeQGUI.java**）の定数宣言部分も変更する。

``` java
public final int ROWS = 10;
public final int COLUMNS = 16;
```

MazeQMainを実行する場合は、**MazeBasic.java**の最短ステップ数も変更する。最短ステップ数は、ゴールまでの最短経路を通った時にかかるステップ数のこと。計算しなくても、上記MainMazeの幅優先探索を実行することで求められる。

``` java
public int firstestSteps = 38; //最短ステップ
```
