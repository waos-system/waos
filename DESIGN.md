# Dev Notes — デザイン仕様書

技術ブログのデザイン原則・カラー・コンポーネント・レイアウト規則をまとめたリファレンスドキュメントです。

---

## 目次

1. [デザイン哲学](#デザイン哲学)
2. [カラーパレット](#カラーパレット)
3. [タイポグラフィ](#タイポグラフィ)
4. [スペーシング](#スペーシング)
5. [コンポーネント仕様](#コンポーネント仕様)
6. [ページレイアウト](#ページレイアウト)
7. [ダークモード](#ダークモード)
8. [レスポンシブ対応](#レスポンシブ対応)
9. [アクセシビリティ](#アクセシビリティ)
10. [アニメーション](#アニメーション)
11. [認証 UI](#認証-ui)

---

## デザイン哲学

### 3つのコアバリュー

| バリュー | 説明 |
|---------|------|
| **Readable First** | コンテンツが主役。装飾は最小限に抑え、読みやすさを最優先する |
| **Technical Precision** | 開発者向けブログとして、コードブロックや技術図表が美しく表示される |
| **Calm & Focused** | ユーザーの集中を妨げない静的なデザイン。不要なアニメーションは排除 |

### デザインの禁止事項

- ✗ グラデーション背景（ブランドグラデーションバーを除く）
- ✗ ボックスシャドウの多用（カード hover 時の微細なシャドウのみ許可）
- ✗ 装飾的なアイコンの乱用
- ✗ 3 色以上のカラーをひとつのコンポーネント内で使用
- ✗ フォントサイズ 11px 未満

---

## カラーパレット

### ブランドカラー (Blue)

```
blue-50:  #eff6ff  — 背景のアクセント・タグ背景
blue-100: #dbeafe  — ホバー背景
blue-500: #3b82f6  — ボーダーアクセント
blue-600: #2563eb  — ★ プライマリアクション（ボタン・ロゴ・リンク）
blue-700: #1d4ed8  — ホバー状態のプライマリ
blue-800: #1e40af  — ダークモードでのアクセント
```

### ニュートラル (Slate)

```
slate-50:  #f8fafc  — ライトモード背景
slate-100: #f1f5f9  — サブ背景・ホバー
slate-200: #e2e8f0  — ボーダー (light)
slate-400: #94a3b8  — プレースホルダー・メタ情報
slate-500: #64748b  — サブテキスト
slate-600: #475569  — セカンダリテキスト
slate-700: #334155  — ボディテキスト (light)
slate-800: #1e293b  — ダークモード サブ背景
slate-900: #0f172a  — ★ ダークモード背景 / ライトモード見出し
slate-950: #020617  — ダークモード フッター背景
```

### セマンティックカラー

```
green-500  / green-50  / green-200  — 成功・承認済み
red-500    / red-50    / red-200    — エラー・危険
amber-500  / amber-100             — 警告・管理者バッジ
orange-500                          — RSS アイコン hover
```

### カラーの使用ルール

- **ボーダー**: `border-slate-200 dark:border-slate-700` を標準とする
- **カード背景**: `bg-white dark:bg-slate-800`
- **ページ背景**: `bg-slate-50 dark:bg-slate-900`
- **プライマリボタン**: `bg-blue-600 hover:bg-blue-700 text-white`
- **セカンダリボタン**: `border border-slate-300 hover:bg-slate-50`

---

## タイポグラフィ

### フォント

| 用途 | フォント | CSS 変数 |
|------|---------|---------|
| 本文・UI テキスト | Noto Sans JP | `var(--font-noto)` |
| コードブロック | Fira Code | `var(--font-fira)` |

### フォントサイズスケール

```
text-xs   (12px) — メタ情報・ラベル・タイムスタンプ・バッジ
text-sm   (14px) — ナビゲーション・カード説明・フォームラベル
text-base (16px) — 本文（prose）
text-lg   (18px) — セクション見出し
text-xl   (20px) — 記事カードタイトル（フィーチャー）
text-2xl  (24px) — ページ見出し（About, Auth）
text-3xl  (30px) — 記事詳細タイトル
text-4xl  (36px) — ホームヒーロー見出し
```

### フォントウェイト

```
font-normal   (400) — 本文・説明テキスト
font-medium   (500) — ナビゲーション・カード説明強調
font-semibold (600) — ページタイトル・ロゴ
font-bold     (700) — 記事タイトル・セクション見出し
font-black    (900) — 404 エラーナンバー
```

### 行間

```
leading-tight   (1.25) — 見出し（複数行タイトル）
leading-snug    (1.375) — カードタイトル
leading-relaxed (1.625) — 本文・説明テキスト
leading-loose   (2.0)  — 目次リスト
```

---

## スペーシング

### レイアウトコンテナ

```
max-w-4xl (896px) — コンテンツ最大幅（全ページ共通）
px-4 sm:px-6      — 水平パディング（モバイル 16px / デスクトップ 24px）
py-10 sm:py-14    — 垂直パディング（モバイル 40px / デスクトップ 56px）
```

### コンポーネント内スペーシング

```
p-4   (16px) — 小カード
p-5   (20px) — 標準カード
p-6   (24px) — 大カード
p-8   (32px) — フィーチャーカード・モーダル

gap-2 (8px)  — タグ間隔
gap-3 (12px) — アイテム間
gap-4 (16px) — カードグリッド
gap-5 (20px) — コメントリスト
gap-6 (24px) — セクション内
gap-8 (32px) — About ページプロフィール
gap-12 (48px) — 記事詳細: 本文 + サイドバー
```

---

## コンポーネント仕様

### カード (ArticleCard)

**通常カード**
```
bg-white dark:bg-slate-800
border border-slate-200 dark:border-slate-700
rounded-xl (12px)
p-5
hover: border-blue-300 dark:border-blue-600 + shadow-md
transition-all duration-200
```

**フィーチャーカード**
```
bg-white dark:bg-slate-800
rounded-2xl (16px)
border: 2px solid blue-600 → 通常と区別
グラデーションバー (from-blue-600 to-indigo-600) を上部に配置
```

### タグバッジ (TagBadge)

```
bg-blue-50 dark:bg-blue-900/30
text-blue-700 dark:text-blue-300
border border-blue-100 dark:border-blue-800
px-2 py-0.5 rounded-md
text-xs font-medium
```

### ボタン

**プライマリ**
```
bg-blue-600 hover:bg-blue-700
text-white font-medium
px-5 py-2.5 rounded-lg
transition-colors
disabled: opacity-50 cursor-not-allowed
```

**セカンダリ（アウトライン）**
```
border border-slate-200 dark:border-slate-700
text-slate-600 dark:text-slate-400
hover:bg-slate-50 dark:hover:bg-slate-800
px-5 py-2.5 rounded-lg
```

**デストラクティブ（ログアウト）**
```
text-red-600 dark:text-red-400
hover:bg-red-50 dark:hover:bg-red-900/20
```

### フォーム要素

**テキストインプット / テキストエリア**
```
w-full rounded-lg
border border-slate-300 dark:border-slate-600
bg-white dark:bg-slate-700 (または slate-800)
px-3.5 py-2.5 text-sm
placeholder-slate-400
focus:outline-none focus:ring-2 focus:ring-blue-500
transition
```

**エラー状態**
```
border-red-400 dark:border-red-600
エラーメッセージ: text-xs text-red-500
```

### ヘッダー

```
sticky top-0 z-50
bg-slate-50/90 dark:bg-slate-900/90
backdrop-blur-md
h-14
スクロール時: border-b + shadow-sm を追加
```

**ユーザーメニュー（ログイン済み）**
```
アバター: w-7 h-7 rounded-full bg-blue-600 text-white
ドロップダウン: bg-white dark:bg-slate-800 rounded-xl border shadow-lg
管理者バッジ: bg-amber-100 text-amber-700 text-[10px]
```

### Callout（MDX コンポーネント）

```
info:    border-blue-300  bg-blue-50  dark:bg-blue-900/20
warning: border-yellow-300 bg-yellow-50 dark:bg-yellow-900/20
tip:     border-green-300  bg-green-50  dark:bg-green-900/20
danger:  border-red-300   bg-red-50   dark:bg-red-900/20

border (左のみ 4px) + rounded-r-xl
p-4 my-6 text-sm
```

### TOC (目次)

```
sticky top-24（ヘッダー高さ 56px + 余白）
text-sm
アクティブリンク: text-blue-600 border-l-2 border-blue-500
非アクティブ: text-slate-500 border-l-2 border-transparent pl-3
```

---

## ページレイアウト

### トップページ（記事一覧）

```
┌─────────────────────────────────────────┐
│ ヒーローセクション（1ページ目のみ）        │
│ h1 + キャッチコピー                      │
├─────────────────────────────────────────┤
│ タグフィルター（横スクロール対応）         │
├─────────────────────────────────────────┤
│ フィーチャーカード（featured: true の記事）│
├─────────────────────────────────────────┤
│ 記事グリッド (1col → 2col sm:)           │
│ ┌──────────┐ ┌──────────┐              │
│ │  Card    │ │  Card    │              │
│ └──────────┘ └──────────┘              │
├─────────────────────────────────────────┤
│ ページネーション（中央揃え）               │
└─────────────────────────────────────────┘
```

### 記事詳細ページ

```
┌─────────────────────────────────────────┐
│ パンくずリスト                           │
├────────────────────────────┬────────────┤
│ 記事本文 (1fr)             │ サイドバー  │
│ ┌──────────────────────┐   │ (200px)    │
│ │ タグ                 │   │            │
│ │ タイトル (h1)        │   │ sticky     │
│ │ メタ情報             │   │ top-24     │
│ │ ─────────────────── │   │            │
│ │ MDX コンテンツ       │   │ 目次       │
│ │                      │   │ (TOC)      │
│ │ タグ（フッター）     │   │            │
│ │ コメントセクション   │   │            │
│ └──────────────────────┘   │            │
├────────────────────────────┴────────────┤
│ 関連記事（3カラム）                      │
├─────────────────────────────────────────┤
│ 一覧へ戻るボタン（中央）                 │
└─────────────────────────────────────────┘

※ サイドバーは lg: (1024px) 以上のみ表示
```

### 認証ページ（ログイン・登録）

```
min-h-[80vh] flex items-center justify-center
最大幅: max-w-sm (384px)

┌────────────────────────────┐
│ ロゴ + タイトル（中央）    │
├────────────────────────────┤
│ フォームカード             │
│ bg-white rounded-2xl       │
│ border shadow-sm           │
│                            │
│  [フォームフィールド]      │
│  [エラーメッセージ]        │
│  [送信ボタン (w-full)]     │
└────────────────────────────┘
│ 補助リンク（中央）         │
```

---

## ダークモード

### 切り替え方式

- **LocalStorage** に `theme: 'dark' | 'light'` を保存
- `<html>` の `class="dark"` で Tailwind の `dark:` バリアントを制御
- **フラッシュ防止**: `layout.tsx` の `<head>` 内にインラインスクリプトで初期クラスを設定

### 各要素のダークモード対応

| 要素 | ライト | ダーク |
|------|--------|--------|
| ページ背景 | `bg-slate-50` | `bg-slate-900` |
| カード背景 | `bg-white` | `bg-slate-800` |
| フッター背景 | `bg-white` | `bg-slate-950` |
| 見出しテキスト | `text-slate-900` | `text-slate-100` |
| ボディテキスト | `text-slate-700` | `text-slate-300` |
| メタテキスト | `text-slate-500` | `text-slate-400` |
| ボーダー | `border-slate-200` | `border-slate-700` |
| インプット背景 | `bg-white` | `bg-slate-700` |

---

## レスポンシブ対応

### ブレークポイント

```
sm: 640px  — モバイル → タブレット
lg: 1024px — タブレット → デスクトップ
```

### レスポンシブ切り替え表

| 要素 | モバイル (< 640px) | デスクトップ (≥ 640px) |
|------|---------------------|----------------------|
| ナビゲーション | ハンバーガーメニュー | 横並びリンク |
| 記事グリッド | 1カラム | 2カラム |
| 記事詳細 | 本文のみ | 本文 + 目次サイドバー |
| ヒーロー見出し | `text-3xl` | `text-4xl` |
| About プロフィール | 縦並び | 横並び (flex-row) |
| フッターリンク | 縦並び | 3カラムグリッド |

---

## アクセシビリティ

### 必須実装項目

- すべての `<img>` に `alt` 属性
- インタラクティブ要素に `aria-label`（アイコンのみのボタン）
- フォーム要素に `<label>` と `for/id` の紐付け
- ページ遷移時のフォーカス管理（Next.js が自動対応）
- `role="alert"` をエラーメッセージに付与
- `aria-expanded` をドロップダウンに付与
- カラーコントラスト比 4.5:1 以上（WCAG AA 準拠）

### キーボードナビゲーション

- すべてのインタラクティブ要素が Tab キーでフォーカス可能
- `focus:ring-2 focus:ring-blue-500` でフォーカスリングを表示
- ドロップダウンは Escape キーで閉じられる（推奨実装）

---

## アニメーション

### 使用ルール

- アニメーションは「情報の変化を示すため」にのみ使用
- **純粋な装飾目的のアニメーションは禁止**
- `prefers-reduced-motion` に対応すること

### 定義済みアニメーション

**フェードイン（記事一覧）**
```css
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}
.animate-fade-in {
  animation: fadeIn 0.4s ease-out forwards;
}
```
使用箇所: 記事一覧グリッド、フィーチャーカード

**スピナー**
```
animate-spin — ボタンローディング状態、Skeleton ローダー
```

**スケルトンローダー**
```
animate-pulse — コメント読み込み中のプレースホルダー
```

**ホバートランジション**
```
transition-colors duration-200 — 色の変化
transition-all duration-200    — 複合プロパティ（カードホバー）
transition                     — デフォルト（150ms ease）
```

---

## 認証 UI

### 認証フロー

```
未ログイン状態
  └─ コメントセクション → ログイン誘導バナー
       └─ [ログイン] ボタン → /auth/login?redirectTo=/blog/{slug}
            └─ ログイン成功 → redirectTo のページに戻る
       └─ [新規登録] ボタン → /auth/register
            └─ 登録完了 → メール確認ページ
                 └─ メール確認 → /auth/callback → ログイン状態に

ログイン済み状態
  └─ ヘッダー: アバター + 表示名 + ユーザーメニュー
  └─ コメントセクション: 投稿フォーム（表示名付き）
  └─ ユーザーメニュー: ログアウト
```

### コメント投稿の認証フロー

```
1. ユーザーがコメントを入力して送信
2. CommentSection が supabase.auth.getSession() でアクセストークンを取得
3. /api/comments に POST（Authorization: Bearer {token}）
4. API Route が supabase.auth.getUser(token) でユーザー検証
5. 検証成功 → DB に insert（is_approved: false）
6. 管理者が Dashboard または pending_comments ビューで承認
7. is_approved: true になったコメントが表示される
```

### 管理者権限

管理者ユーザーは `user_metadata.role === 'admin'` で識別されます。
- ヘッダーに「管理者」バッジ（amber）を表示
- 将来的な管理者ダッシュボード `/admin` への拡張ポイント

---

## ファイル構成と対応関係

```
デザイントークン
  tailwind.config.ts       ← カラー・フォント・typography 設定
  app/globals.css          ← カスタム CSS クラス・アニメーション・コードハイライト

コンポーネント
  components/Header.tsx    ← ナビゲーション・認証状態表示
  components/Footer.tsx    ← フッターリンク
  components/ArticleCard.tsx  ← 記事カード（通常・フィーチャー）
  components/TableOfContents.tsx  ← TOC + スクロールスパイ
  components/CommentSection.tsx   ← コメント（認証ゲート付き）
  components/ViewCounter.tsx      ← 閲覧数

ページ
  app/page.tsx             ← トップページレイアウト
  app/blog/[slug]/page.tsx ← 記事詳細レイアウト
  app/about/page.tsx       ← About ページレイアウト
  app/auth/login/page.tsx  ← ログインフォーム
  app/auth/register/page.tsx ← 登録フォーム
```
