
Vue.jsへ`Pug`を導入するためのサンプルコード（リポジトリ）

## 概要

参照URLはこちら - [Vue Loader#Pug](https://vue-loader.vuejs.org/guide/pre-processors.html#pug)

## 導入手順

### `pug`,`pug-plain-loader`の導入

```bash
# Vue.jsのプロジェクト作成
vue init webpack-simple vue-pug-sample

# Pugの導入
yarn add pug pug-plain-loader
```

### webpack.config.jsへの追記

```javascript
module.exports = {
  module: {
    rules: [
      // ここから
      {
        test: /\.pug$/,
        loader: 'pug-plain-loader'
      }
      // ここまで
    ]
  }
}
```

### *.vueのテンプレート構文を`Pug`記法に修正

「src/App.vue」を例にbefore,afterを記載。

#### before

```html
<template>
  <div id="app">
    <img src="./assets/logo.png" />
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
  </div>
</template>
```

#### after

```html
<template lang="pug">
  #app
    img(src='./assets/logo.png')
    h1 {{ msg }}
    h2 Essential Links
    ul
      li
        a(href='https://vuejs.org', target='_blank') Core Docs
      li
        a(href='https://forum.vuejs.org', target='_blank') Forum
      li
        a(href='https://chat.vuejs.org', target='_blank') Community Chat
      li
        a(href='https://twitter.com/vuejs', target='_blank') Twitter
    h2 Ecosystem
    ul
      li
        a(href='http://router.vuejs.org/', target='_blank') vue-router
      li
        a(href='http://vuex.vuejs.org/', target='_blank') vuex
      li
        a(href='http://vue-loader.vuejs.org/', target='_blank') vue-loader
      li
        a(href='https://github.com/vuejs/awesome-vue', target='_blank') awesome-vue
</template>
```

### 実行

この後、`yarn run dev`で問題なく表示できればOK。
