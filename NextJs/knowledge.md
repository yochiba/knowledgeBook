# Next.js関連


## SSR, SSG(pre-renderingの方法の違い)
***

By default, Next.js pre-renders every page.  
This means that Next.js generates HTML for each page in advance, instead of having it all done by client-side JavaScript.   
Pre-rendering can result in better performance and SEO.
<br><br>

SSRとSSGは各ページごとに使い分けることができる。
<br><br>

- ## Server Side Rendering
  各リクエストごとにHTMLを生成する。  
  ページ内部のデータが頻繁にアップデートされるページの場合はSSRを採用すると良い。  
  (対象のページはユーザからのリクエストより事前にページをレンダリングしても問題はない？)
  ***
<br>

- ## Static Site Generation
  ビルド時にHTMLを生成する。プリレンダリングされたHTMLは各リクエストごとに再利用される。  
  ページ内部のデータが頻繁にアップデートされないページの場合はSSG。  
  (対象のページはユーザからのリクエストより事前にページをレンダリングしても問題はない？)  
***
<br>

  ## static generationで外部データを取得してビルドするには？

  getStaticPropsは以下の内容で実行される。
  - production環境でのビルド時に外部のデータをフェッチする
  - 取得したデータはPropsに送信される。
```
  export default function Home(props) { ... }

  export async function getStaticProps() {
  // Get external data from the file system, API, DB, etc.
  const data = ...

  // The value of the `props` key will be
  //  passed to the `Home` component
  return {
    props: ...
  }
}
```

<br><br><br>

## Next.jsアプリケーションの作成(create-next-app)
***
```
yarn create next-app {application name}
```
<br>

## Typescriptの導入
***
  1. Typescript関連のプラグインを導入する。
```
yarn add -D typescript @types/react @types/node
```
  2. tsconfig.jsonを作成。
```
touch tsconfig.json
```
  3. jsファイルをts/tsxファイルにリネームする。
```
mv ./pages/index.js ./pages/index.tsx
mv ./pages/_app.js ./pages/_app.tsx
mv ./pages/api/hello.js ./pages/api/hello.ts
```
<br>

***

## Sassの導入
***
  1. Sass関連のプラグインを導入
```
yarn add -D sass
```
  2. cssファイルをscssファイルに変換
```
mv ./styles/Home.module.css ./styles/Home.module.scss
mv ./styles/globals.css ./styles/globals.scss
```

  3. cssファイルでimportされている記述箇所をscssに修正。(初期状態であれば以下の2ファイル)
```
./pages/index.tsx
./pages/_app.ts
```
<br>

***

## gray-matterの導入
  - マークダウンでブログページを作成できるようにするプラグイン

```
yarn add -D gray-matter
```

<br>

***
## 公式サイト
***
```
https://nextjs.org/
```