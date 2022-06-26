# SteamApp日本語化ガイド(Xunity.AutoTranslatorのインストール for Mac)

## はじめに（超重要）
これはあくまでReiPatcherが使えないMac環境向けにReiPatcherを使わない手順をまとめたものです。  
そもそも日本語化公開者の方がReiPatcherの方法しか公開されていないのであればそれが日本語化公開者の方がサポートできる唯一の手順になります。  
こちらの方法を参考にして日本語化公開者の方に質問されるなど、ご迷惑をおかけすることのないようお願いします。

## 概要
Steamアプリの日本語化において、オールインワンで便利なのでXunity.AutoTranslator-ReiPatcherで配布される場合が多いです。  
※便利な(導入がシンプルになる)ツールは使うべきなので、これは良いことだと思います。  
ただしReiPatcherはWindows版なのてMac版Steamではその手順が使えません。  
従ってMacでReiPatcherを使わずにXunity.AutoTranslatorを導入する方法をまとめました。  
というか単に自分が忘れがちなのでメモ用途として記録です。

## 免責
- 自分用メモなのでサポートしません。  
※ローカルライブラリのインストールにつまづくと各自の環境の問題になりやすく、解決にかなり苦戦することを知っているためです。
- 2022年6月19日時点でのメモ書きです。  
OSのアップデートやライブラリのバージョンが変わったらふるまいが変わる可能性があるのでその場合は使えないかもしれません。  
ご了承ください。
- 動作確認しているのはグルームヘイヴン、イーオンズエンドです

## 重要
- ここに書いたのはあくまで簡略化した日本語メモです。
- 正式にはそれぞれのライブラリのインストールガイドを参考にして作業を進めてください。
- 3, 4, 5の設定ファイル/翻訳ファイルについては日本語化公開者が公開されているやり方に合わせて変更する必要があります
- 「はじめに」にも書きましたが、これを前提として日本語化公開者の方に問い合わせるなど、ご迷惑をおかけすることのないようお願いします。

## もくじ
1. BepInEx Managerのインストール
2. Xunity.AutoTranslatorのインストール
3. フォントの設置
4. 設定ファイルの変更
5. 翻訳ファイルの設置
6. 起動

## BepInEx Managerのインストール
https://docs.bepinex.dev/articles/user_guide/installation/index.html?tabs=tabid-nix
- ダウンロードする
- インストール先はアプリのフォルダ  
Steamより当該アプリの管理 > ローカルファイルを閲覧にてアプリフォルダの所在確認ができる  
（~/Library/Application Support/Steam/steamapps/cojmon/$app_name だと思います。）
- run_bepinex.shを編集  
executable_nameに$app_nameを入力
- 権限変更  
chmod u+x run_bepinex.sh
- Steamの起動オプション追加  
Steamより当該アプリのプロパティ > 起動オプション  
"/Users/seimiyajun/Library/Application Support/Steam/steamapps/common/$app_name/run_bepinex.sh" %command%
- 一度実行して、セキュリティ的な問題がないか確認する  
（Macのセキュリティで、インターネットからダウンロードしたアプリはそのままでは起動しないため）

## Xunity.AutoTranslatorのインストール
インストール手順： https://github.com/bbepis/XUnity.AutoTranslator#bepinex-plugin  
ダウンロードファイル置き場： https://github.com/bbepis/XUnity.AutoTranslator/releases  
- BepInEx版をダウンロードする
- インストール先はアプリのフォルダ  
アプリフォルダはBepInEx Managerのインストール手順を参照  
zipを解凍したらフォルダ構成が出てくるので、それぞれの中身をアプリフォルダのBepInExのフォルダに『追加』する
- 一度起動して、アプリを落とす  
※一度起動すると設定ファイルがつくられる。  
アプリを落とす

## フォントの設置
1. 使いたいフォントをコピー  
　使いたいフォントが特になければUnityAutoTranslatorで配布している TMP_Font_AssetBundles.zip を展開して使うと良いかも。
2. Steamの当該アプリのアイコンを右クリック > パッケージの内容を表示
3. そのルートにフォントをペースト

## 設定ファイルの変更
設定ファイル： $app_path/BepInEx/config/AutoTranslatorConfig.ini  
変更箇所は下記の通り※実際に使う設定に合わせてください。
- Service > Endpoint：値を削除してblankにする
- General > Language：ja
- General > FromLanguage：en
- Behaviour > FallbackFontTextMeshPro：設置したフォントのファイル名　

## 翻訳ファイルの設置
$app_path/Translation/ja/Text あたりに日本語化テキストファイルを設置する

## 起動
動作するはず！
