# 共通指示
- 日本語の文章における句読点には必ずカンマ「，」とピリオド「．」を使用する．
- 文章は「である調」を用い論文を意識して記述する．
- `.cls` ファイルなどを編集しフォーマットを変更しないでください

# 数式の記述方法
- 数式は必ずTeX表記（equation，align，$ inline $）を使用し，式中の変数は必ず説明する．
- equationやalignの中で数式を記述する際は，適時インデントを加えソースの可読性を担保してください．
- $ inline $ の中で数式を記述する際は，$ (ドルマーク)の前後で空白を加えソースの可読性を担保してください．

- 数学的対象を記述する際は下記のルールに従い記述してください
  
| 数学的対象 | ルール | 記法の例 |
| :--- | :--- | :--- |
| スカラー (変数の場合) | 小文字・斜体 | x |
| スカラー (定数の場合) | 大文字・斜体 | X |
| ベクトル | 小文字・太字 | {\mathbf x} | 
| 行列・テンソル | 大文字・太字 | {\mathbf X} |
| 確率分布 | 大文字・スクリプト体 | {\mathcal N} |
| 集合 | 大文字・中抜き | {\mathbb X} |
| 関数 | 小文字・斜体 | f |

例) 
```text
全結合層を(\ref{eq_Dense})に示す．

\begin{equation}
  {\mathbf y}_i = f_i ( {\mathbf y}_{i - 1} {\mathbf W}_i + {\mathbf b}_i )
  \label{eq_Dense}
\end{equation}

\noindent
ここで$ {\mathbf y}_i \in {\mathbb R}^{1 \times D_i} $が$ i $層目の全結合層の出力，$ {\mathbf W}_i \in {\mathbb R}^{D_{i - 1} \times D_i} $が$ i $層目の全結合層の重み行列，$ {\mathbf b}_i \in {\mathbb R}^{1 \times D_i} $が$ i $層目の全結合層のしきい値ベクトル，$ f_i: {\mathbb R}^{1 \times D_i} \to {\mathbb R}^{1 \times D_i} $が$ i $層目の活性化関数，$ D_i $が$ i $層目の全結合層のニューロン数である．
```

# TeXのコンパイル
- TeXレポートの作成が依頼された場合，その環境にはTeX-Live-Fullがインストールされており，下記のコマンドでコンパイルできます．
```text
latexmk -pdfdvi main.tex
latexmk -C
```

# TeXレポート
- TeXレポートはcursorの終了時に作成する `report.md` とは別物で，人間からの指示があった場合にのみ作成してください
- TeXレポートの作成が依頼された場合，`cursor-TeX/templates/Report` 内のTeXファイル等をプロジェクトのルートにコピーし，これを編集てPDFのレポートを作成してください
- この際，フォルダ名はレポートの内容に応じ適時変更してください

# TeXスライド
underconstruction

# ディレクトリ構造の例
```text
.
├── cursor-template/         # cursorへの指示等やTeXレポートのテンプレートをまとめたリポジトリ
│   ├── root_prompt.md       # プログラムの指示が書かれたドキュメント
|   └── prompts/             # それぞれのタスクの指示が書かれたプロンプトがまとめられたフォルダ
│       └── tex.py           # TeXの指示が書かれたドキュメント
│
├── cursor_TeX/              # TeXテンプレートがまとめられたリポジトリ
│   ├── README.md            # 文章を書く際の注意事項がまとめられたドキュメント
│   └── TeX_templates/       # TeXテンプレートがまとめられたフォルダ
│       └── Report               # レポートのテンプレート
│           ├── main.tex         # latexでコンパイルするソース
│           ├── sections/        # レポートの章ごとに分けられたソースをまとめたフォルダ
│           │   └── 01_introdcution.tex             # ソースは章ごとに分割する
│           └── figures/         # レポートの画像をまとめたフォルダ
```
