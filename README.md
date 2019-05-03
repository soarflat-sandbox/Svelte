# Svelte

Svelte 3と戯れる。

## Svelteとは?

>Svelteはユーザーインターフェースを構築するための急進的な新しいアプローチです。 ReactやVueのような伝統的なフレームワークはブラウザの中でそれらの仕事の大部分をするのに対して、Svelteはあなたがあなたのアプリケーションを構築するとき起こるコンパイルステップにその仕事を移します。

>Svelteは、実行時にアプリケーションコードを解釈するのではなく、構築時に理想的なJavaScriptに変換します。

>Svelteを使ってアプリ全体を構築することも、既存のコードベースに段階的に追加することもできます。従来のフレームワークへの依存によるオーバーヘッドなしに、どこでも動作するスタンドアロンパッケージとしてコンポーネントを出荷することもできます。

## quick start

```shell
npx degit sveltejs/template my-svelte-project
cd my-svelte-project
npm install
npm run dev & open http://localhost:5000
```

## Svelteの基礎知識

### コンポーネント（`.svelte`ファイル）

Svelteでは、コンポーネントを`.svelte`という拡張子のファイルに定義する。

以下はコンポーネントの単純な例。HTML、CSS、JavaScriptをまとめて定義する。

CSSのスタイルはこのコンポーネントだけに影響される。

```js
<script>
	let name = 'world';
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}!</h1>
```

以下のように変数を定義し、

```js
let name = 'world';
```

以下のようにHTMLを記述すれば、変数を参照できる。

```html
<h1>Hello {name}!</h1>
```

### コンポーネントをimportして利用する

```js
<script>
	import Nested from './Nested.svelte';
</script>

<p>This is a paragraph.</p>
<Nested/>
```

### アクセシビリティ

```js
<script>
	let src = 'tutorial/image.gif';
</script>

<img src={src}>
```

```
A11y: <img> element should have an alt attribute (5:0)
```

```html
<img src={src} alt="A man dancing">
```

属性名と変数名が同じ場合、以下のようにショートハンドが利用できる。

```html
<img {src} alt="A man dancing">
```

### HTML文字列をレンダリングする

Svelteでは以下のような文字列をプレーンな文字列としてレンダリングされる。

```js
<script>
	let string = `this string contains some <strong>HTML!!!</strong>`;
</script>

<p>{string}</p> // this string contains some <strong>HTML!!!</strong>
```

HTML文字列をレンダリングしたい場合は、`{@html ...}`を利用する。

```js
<script>
	let string = `this string contains some <strong>HTML!!!</strong>`;
</script>

<p>{@html string}</p>
```

### コンポーネントを利用する

以下のように`new`を利用すれば、コンポーネントを好きな箇所で利用できる。

```
import App from './App.svelte';

const app = new App({
	target: document.body,
	props: {
		// we'll learn about props later
		answer: 42
	}
});
```

### ビルドツール

メジャーなビルドツールを利用すれば、Svelteのビルドは可能。

- Rollup: [rollup-plugin-svelte](https://github.com/rollup/rollup-plugin-svelte)
- webpack: [svelte-loader](https://github.com/sveltejs/svelte-loader)
- Parcel: [parcel-plugin-svelte](https://github.com/DeMoorJasper/parcel-plugin-svelte)


## まだ公開されていない公式のブログポスト

- [Svelte for new developers](https://svelte.dev/blog/svelte-for-new-developers)
- [Setting up your editor](https://svelte.dev/blog/setting-up-your-editor)