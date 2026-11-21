# Detent 単語データ（TSL・NAWL 日本語版）

英単語アプリ「Detent: 触って覚える英単語」（iPhone）に同梱している単語データです。TOEIC Service List（TSL）1.2 と New Academic Word List（NAWL）1.2 の各見出し語に、日本語訳・品詞・例文（英語と和訳）・用法メモを付けています。

## ライセンス

このデータは [Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）](https://creativecommons.org/licenses/by-sa/4.0/) で公開します。元のリストと同じライセンスです。改変・再配布・商用利用ができます。改変したものを配布するときは、同じライセンスで公開し、下の帰属表示を含めてください。

アプリに同梱しているデータにも、このライセンスが適用されます。App Store の標準使用許諾（EULA）の制限は、このデータには及びません。

## 帰属表示（元のリスト）

- **TOEIC Service List (TSL) 1.2** by Browne, C. and Culligan, B. — CC BY-SA 4.0
- **New Academic Word List (NAWL) 1.2** by Browne, C., Culligan, B., and Phillips, J. — CC BY-SA 4.0
- 取得元：https://www.newgeneralservicelist.com/ （取得日 2026-10-18）

**改変の内容**：見出し語の選択・順序は元のリストに従い、各語に日本語訳（glossShort・glosses）、品詞（pos）、英語の例文と和訳（example）、用法メモ（note）を付加しました。NAWL の出題順（order）は、学術英語での出会いやすさの推定値に基づきます。次の語は収録していません。

- NAWL の接頭辞8語と分類不明1語、接頭辞に近い neo
- 正解すると祝う演出（音・触覚・光）が出るアプリのため、自殺・性・奴隷制を主な意味とする4語（suicide, sexuality, sperm, slavery）。一覧と理由は `data/excluded.json`

見出し語は3語だけ変えています。NAWL の founds は found（設立する）に、TSL の pant は pants（ズボン）に、housekeep は housekeeping（客室清掃）にしました。TOEIC で出会うのはほぼこの形だと判断したためです。

## ファイル

| ファイル | 内容 |
|---|---|
| `data/tsl.csv` | TSL 1,250語（1語1行） |
| `data/nawl.csv` | NAWL 945語（1語1行。TSL と共通の229語を含む） |
| `data/tsl.json`・`data/nawl.json` | アプリに同梱している形式。両方のリストに載る語は `tsl.json` に1回だけ入れ、`alsoIn` に NAWL での順番を書いています（合計1,966語） |
| `data/excluded.json` | 収録しなかった語と理由 |
| `process/GEN_SPEC.md` | 生成の仕様（第1段階） |
| `process/VERIFY_SPEC.md` | 検証の仕様（第2段階） |
| `process/changes/*.json` | 検証で直した語の記録。`final_adjudication.json` は最終確認（辞書照合で食い違った語・両リスト共通語の統合・無料で使える語の見直し）で直した語 |
| `process/crosscheck.json` | 英和辞書 EJDict-hand（CC0）・NAWL 公式の日本語訳との自動照合の結果 |

CSV の列：order（リスト内の順番。TSL は頻度順位）、headword、pos、gloss_short（4択で使う訳）、glosses、example_en、example_ja、note、free_in_app（アプリで無料の語）、also_in（もう一方のリストにも載る語）。

## 作り方と品質について

訳・例文は AI（Anthropic の Claude）で作成し、作成とは別の担当（AI）による独立の検証と、英和辞書・公式の日本語訳との自動照合を行っています。照合で食い違った語は、もう一度見直しています。市販の単語帳・辞書の訳や例文は使っていません。それでも誤りが残っている可能性があります。誤りを見つけたら Issue でお知らせください。更新でまとめて直します。

## 商標

TOEIC および TOEFL は ETS の登録商標です。このデータとアプリは ETS および IIBC の検討・承認を受けたものではありません。
