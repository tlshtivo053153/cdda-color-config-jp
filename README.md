# Cataclysm:DDA 色設定
Cataclysm:DDAの色テーマ、色設定テンプレート。

私は色に関する専門知識はないため、専門的には間違っている内容があるかもしれないことに注意。

## 導入方法

1. `Code -> Download ZIP` からダウンロードして展開する。
2. `data` フォルダをゲームを実行ファイルのあるフォルダにコピーする。

### 色のRGB値を変更する"色テーマ"

`タイトル画面->設定->文字色` を開く。
`c` キーから色テーマを選び、
再起動することで反映される。
`f` キーでフィルタも可能。
今回、導入したテーマは以下の5つである。

#### base_colors-bright.json
暗い色を全体的に明るく変更。

![bright](https://raw.githubusercontent.com/tlshtivo053153/cdda-color-config-jp/images/bright.png)

#### base_colors-bright_blue.json
上記の `base_colors-bright.json` から青色を更に明るく見えるように調整。

![bright blue](https://raw.githubusercontent.com/tlshtivo053153/cdda-color-config-jp/images/bright_blue.png)

#### base_colors-accessibility.json
![ここ](https://jfly.uni-koeln.de/colorset/)のカラーユニバーサルデザイン推奨配色セットを参考に作成。

![accessibility](https://raw.githubusercontent.com/tlshtivo053153/cdda-color-config-jp/images/accessibility.png)

#### base_colors-solarized.json
テキストエディタによく使われているカラーパレットsolarizedを参考にして作成。

![solarized](https://raw.githubusercontent.com/tlshtivo053153/cdda-color-config-jp/images/solarized.png)

#### base_colors-solarized_black.json
上記の `base_colors-solarized.json` より黒のRGB値を暗く設定した。

![solarized black](https://raw.githubusercontent.com/tlshtivo053153/cdda-color-config-jp/images/solarized_black.png)

#### デフォルトの色に戻したいとき
デフォルト設定に戻したい場合は、 `base_colors-default.json` を選択する。

#### 複数のテーマを用意した理由
人によって色の見えやすさが異なる他に、ディスプレイの種類、ディスプレイの明るさ、
周囲の明るさによっても色の見えやすさが変わってくると考えたので複数の色テーマを用意した。

### 色の割り当てを変更する"色設定テンプレート"

`タイトル画面->設定->文字色` を開く。
`t` キーから色設定テンプレートを選ぶ。
今回、導入したテンプレートは以下の1つである。

* highlight_black_blue.json
    * 選択中の文字のハイライトを文字色を黒、背景色を青に固定した。

デフォルト設定に戻したい場合は、 `default.json` を選択する。

このテンプレートを用意した理由を説明する。
ゲームのカーソルの位置は背景色を青色にすることで表現している。
そのため、青色のRGB値を明るい色にすればするほどカーソル位置の文字が読みにくくなる。
もし、カーソル位置の文字が読みにくくなるようなら、このテンプレートを利用するか、
`h_色名` と記述してあるところを変更するとよい。(例: `h_black`, `h_cyan`)。
色設定テンプレートの設定ファイルは、 `config/custom_colors.json` にある。

## 自分で色のRGB値の変更をする

色のRGB値の変更方法を説明する。
`config/base_colors.json` をテキストエディタで開く。
以下の内容がデフォルトの設定ファイルである。

```json
[
  {
    "type": "colordef",
    "BLACK": [ 0, 0, 0 ],
    "RED": [ 255, 0, 0 ],
    "GREEN": [ 0, 110, 0 ],
    "BROWN": [ 97, 56, 28 ],
    "BLUE": [ 10, 10, 220 ],
    "MAGENTA": [ 139, 58, 98 ],
    "CYAN": [ 0, 150, 180 ],
    "GRAY": [ 150, 150, 150 ],
    "DGRAY": [ 99, 99, 99 ],
    "LRED": [ 255, 150, 150 ],
    "LGREEN": [ 0, 255, 0 ],
    "YELLOW": [ 255, 255, 0 ],
    "LBLUE": [ 100, 100, 255 ],
    "LMAGENTA": [ 254, 0, 254 ],
    "LCYAN": [ 0, 240, 255 ],
    "WHITE": [ 255, 255, 255 ]
  }
]
```

例として、赤色を明るくしたいとする。
赤色を変更するためには、"RED": で始まる行を変更する。

```json
    "RED": [ 255, 0, 0 ],
```

括弧内の値は、左から R値255、G値0、B値0を表す。
黒色のRGB値は [ 0, 0, 0 ]、白色のRGB値は [ 255, 255, 255 ] である。
変更する値を0に近づければ、黒色に近くなり色は暗くなり、
逆に、255に近づければ、白色に近くなり色は明るくなる。
今回は色を明るくしたいので、G値、B値の値を大きくする。
つまり、以下のように変更する。

```json
    "RED": [ 255, 50, 50 ],
```

変更した `config/base_colors.json` をゲームから選択できるようにするためには
`data/raw/color_themes/` フォルダに配置する。
`base_colors.json` を適切な名前に変更する。

色の確認をしながら変更したい場合は、
「rgb ツール」などのワードで検索を行い、適当なツールを使うとよい。

## 自分で色の割り当てを変更する
`タイトル画面 -> 設定 -> 文字色` から設定する。
見にくい色を `Enter` で選択して、別の色を割り当てる。

変更した設定をゲームから選択できるようにするためには
`config/custom_colors.json`を `data/raw/color_themes/` フォルダに配置する。
`custom_colors.json` を適切な名前に変更する。
