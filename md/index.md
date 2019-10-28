---
title: トップ
---

## はじめに

UI Spec MDは画面仕様書を作成することに特化した静的サイトジェネレーターです。主に次のような機能が備えています。

- ベースは、Github-flavoredマークダウン
- [UI flows](https://signalvnoise.com/posts/1926-a-shorthand-for-designing-ui-flows)によるコードブロックも使用可能
- ファイルの先頭にYaml形式でタイトル、画像のパスなどのメタ情報を定義可能
- 編集サーバー機能により、ブラウザ上でそのまま編集したり、画像をドラッグ&ドロップで配置・更新することが可能

## インストール

```bash
npm install --save-dev ui-spec-md
```

## 使い方

`package.json`に`ui-spec-md`を使ったコマンドを定義します。下記は定義の一例になります。

- `generate`: 公開するためのhtmlを生成する
- `edit-server`: 編集中、ブラウザ上で直接編集するためのサーバーを起動

仮にディレクトリ構成は次のようになっていたとすると、

```
├── dist
│   ├── public（公開ディレクトリ）
│   └── edit（編集サーバーの出力先）
├── md
│   └── (Markdownファイル)
├── package-lock.json
├── package.json
└── theme
    └── standard
        ├──  (テーマファイル)
```

npmのコマンドは次のように定義します。

```json#package.json
{
  // ui-spec-mdの定義例
  "scripts": {
    "generate": "ui-spec-md generate -m md -d dist/public -t theme/standard",
    "edit-server": "ui-spec-md edit-server -m md -d dist/edit",
  }
}
```

`theme`ディレクトリは、下記コマンドを実行することで生成することができます。

```
npx ui-spec-md theme-init
```
