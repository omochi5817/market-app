# 相場 PRO — CLAUDE.md

## プロジェクト概要

Vanilla JS / HTML / CSS のシングルファイル PWA（Progressive Web App）。
すべてのロジック・スタイル・マークアップは `index.html` 1ファイルに収まっている。

- **アプリ名**: 相場 PRO
- **公開 URL**: https://omochi5817.github.io/market-app
- **ホスティング**: GitHub Pages
- **Service Worker**: `sw.js`（オフライン対応、キャッシュ管理）

## タブ構成（6タブ）

| タブ | 用途 |
|------|------|
| 相場 | 現在の相場情報の記録・表示 |
| 地金 | 地金の買取・計算 |
| オークション | オークション出品管理 |
| 金券 | 金券の買取管理 |
| 切手 | 切手の買取管理 |
| 設定 | アプリ設定・データ管理 |

## データ永続化

`localStorage` のみ使用。外部データベース・サーバーサイドストレージは一切なし。

## 技術スタック

- HTML5 / CSS3 / Vanilla JS（フレームワークなし）
- PWA（Web App Manifest + Service Worker）
- Google Fonts（DM Mono）— オフライン時はシステムフォントへフォールバック

## 禁止事項

- **外部 API の追加禁止**: Gemini API、OpenAI API、Anthropic API、Google Apps Script 等の外部 API への依存を新たに追加しないこと
- **ファイル分割禁止**: `index.html` のシングルファイル構成を維持すること（ビルドツール・バンドラー導入禁止）
- **外部ライブラリ追加禁止**: npm パッケージ、CDN 経由のフレームワーク等を追加しないこと
- **Node.js / サーバーサイド処理禁止**: 完全にクライアントサイドで動作すること

## 開発ルール

- すべての変更は `index.html` への直接編集
- `sw.js` のキャッシュバージョン（`CACHE` 定数）はキャッシュ破棄が必要な変更時のみ更新
- `manifest.json` はアプリのメタ情報管理のみ
- モバイルファースト設計（iOS Safari / Android Chrome 対応）
- セーフエリア（`env(safe-area-inset-*)` ）を維持すること

## デプロイ

`main` ブランチへの push で GitHub Pages に自動反映される。
