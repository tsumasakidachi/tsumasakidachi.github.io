---
title: "steamcmd を使った専用サーバの更新ができなくなり Steam クライアントに統合されました"
category: "stormworks"
author: "ツマサキダチ"
layout: "post"
---
steamcmd による Stormworks 専用サーバの更新が利用できなくなりました。パッチノート [v1.9.21 - The Variable Pitch Ship Propeller Update!](https://store.steampowered.com/news/app/573090/view/3881604511640365690) において 2024 年 2 月 16 日にこの機能の提供を終了する事が予告されていました。

# 新しい専用サーバの更新方法

現在専用サーバの実行ファイル (`server.exe` と `server64.exe`) は Steam クライアントによってゲーム クライアントと同じフォルダ (`C:\Program Files (x86)\Steam\steamapps\common\Stormworks`) に配置されており、そのまま実行すれば使えるようになっています。また更新はゲーム クライアントと同じように自動的に行われます。リモート マシンで専用サーバを実行していた場合は Steam をインストールしてログインし Stormworks をインストールするか、自分の PC から全てのファイル (上記フォルダの中身) を転送する必要があります。

# 自作アドオンの追加

ゲーム内で作成したアドオンを組み込むには `server_config.xml` の `playlists` 要素に Stormworks のデータ フォルダ (`%appdata%\Stormworks`) を起点とする相対パスを追加します。以下に例を示します。

```
<playlists>
    <!-- ↓ デフォルト アドオン (ゲーム クライアント フォルダ起点の相対パス) -->
    <path path="rom/data/missions/default_mission_locations"/>
    <!-- ↓ 自作アドオン (ゲーム データ フォルダ起点の相対パス) -->
    <path path="data/missions/auto_authorization"/>
</playlists>
```