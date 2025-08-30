# バーチャルドラムキット（Virtual Drum Kit）

単一の **`index.html`** だけで動く、**WebAudio** ベースのドラムキットSPA。
キーボード＆クリックで演奏、**録音/再生・BPM/メトロノーム・量子化(1/8,1/16)・複数トラック＆ミュート・JSON保存/読み込み** に対応。

> 作品の方向性：**音楽スタジオをテーマ**にした、洗練＆モダンなUI（ダーク／ガラス質感／ネオンアクセント）

---

## デモ

* GitHub Pages で公開したURLをここに貼ってください：

  * 例）`https://<yourname>.github.io/virtual-drum-kit.html/`

---

## 機能

* キー/クリックでパッド演奏（ビジュアル反応）
* **録音／再生**（複数トラックを合成）
* **BPM スライダー＆メトロノーム**
* **量子化**：Off / 1/8 / 1/16（録音時にスナップ）
* **複数トラック**：録音先の選択・ミュート・複製・削除
* **JSON 書き出し／読み込み**（演奏データの保存・復元）

---

## キーマップ

| Key | サウンド                  |
| --- | --------------------- |
| A   | Kick（キック）             |
| S   | Snare（スネア）            |
| D   | Hi‑Hat Closed（ハイハット閉） |
| F   | Hi‑Hat Open（ハイハット開）   |
| H   | Clap（クラップ）            |
| J   | ハイタム                  |
| K   | ロータム                  |
| L   | Crash（クラッシュシンバル）      |

**ショートカット**：`R`=録音/停止、`P`=再生、`Space`=停止、`C`=クリア

---

## 使い方（3ステップ）

1. ページ上部の **「🔈 サウンド有効化」** を1回クリック（ブラウザの音声再生許可）
2. パッドを叩く or キーボードで演奏
3. 録音：`R` → 演奏 → `R` で停止 ／ 再生：`P`

**TIPS**

* まずは **BPM 60〜80** でゆっくり。慣れてきたら 100前後へ。
* 量子化は **1/8 → 1/16 → Off** の順で難易度アップ。
* **Track1=Kick / Track2=Snare / Track3=Hi‑Hat** の役割分担が編集しやすい。

---

## JSONの書き出し／読み込み

* 書き出し：**「⇩ JSON書き出し」** → `drumkit_<timestamp>.json` が保存されます。
* 読み込み：**「⇧ JSON読み込み」** → ファイル選択。

### JSONフォーマット（例）

```json
{
  "version": 1,
  "bpm": 100,
  "quant": "8",   // "off" | "8" | "16"
  "tracks": [
    { "name": "Kick", "muted": false, "events": [
      {"sound": "kick", "at": 0}, {"sound": "kick", "at": 1200}
    ]},
    { "name": "Snare", "muted": false, "events": [
      {"sound": "snare", "at": 600}, {"sound": "snare", "at": 1800}
    ]}
  ]
}
```

* `sound` は `kick|snare|hhc|hho|clap|tom1|tom2|crash`
* `at` は **ミリ秒**（録音開始からの経過時間）

---

## 公開（GitHub Pages）

1. このリポを **Public** で作成（例：`virtual-drum-kit.html`）
2. `index.html` をコミット＆push
3. **Settings → Pages** → Build and deployment: *Deploy from a branch* ／ Branch: `main` ／ Folder: `/ (root)` → **Save**
4. 数十秒後、上部に公開URLが表示されます

更新は `git add -A && git commit -m "update" && git push` だけでOK。

---

## トラブルシューティング

* **音が鳴らない**：

  1. どこかをクリックして音声許可（上部の「🔈 サウンド有効化」）
  2. 端末のミュート解除／音量UP
  3. iOS Safari は低電力モードOFF推奨
* **低音が聴こえづらい（ノートPC内蔵SP）**：イヤホンで確認すると分かりやすいです。
* **Pagesが404**：反映にラグがあります。1〜2分待ってから再読込。`index.html` がリポ直下かも再確認。

---

## カスタマイズ

* **デザイン**：`<style>` の `:root` 変数（カラー）や各クラスを調整
* **キー配列**：`keyToSound` を編集
* **音色**：`playKick/playSnare/...` の中のフィルタやエンベロープを調整
* **セキュリティ（任意）**：`<head>` に CSP(meta) を追加可

  ```html
  <meta http-equiv="Content-Security-Policy"
        content="default-src 'self'; img-src 'self' data:; media-src 'self'; connect-src 'none'; frame-ancestors 'none'; base-uri 'self'; form-action 'none';">
  ```

---

## 動作環境

* 最新版の Chrome / Edge / Safari / Firefox を想定（モバイル含む）
* ブラウザの**自動再生ポリシー**により、**ユーザー操作（クリック/キー）後にAudioが有効化**されます

---

## ライセンス

* デフォルト：**MIT**（変更可）。

  * MITにする場合は、このリポに `LICENSE` を追加してください。

---

## クレジット

* Design & Dev: **shimarin**
* Special Thanks: WebAudio API 💙
