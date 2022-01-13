# eslint-config-pirika

ピリカにおけるESLint共有設定

## 使用方法

### パッケージのインストール

```sh
$ npm install -D eslint-config-pirika
$ npx eslint-config-pirika-install-deps-react # Reactプロジェクトの場合
$ npx eslint-config-pirika-install-deps # それ以外の場合
```

※`eslint-config-pirika-install-deps`/`eslint-config-pirika-install-deps-react`にて、利用プロジェクトに応じた必須コンポーネントを追加インストールする。

### `.eslintrc.js`の設定

```js
module.exports = {
  extends: [
    "eslint-config-pirika/react" // Reactプロジェクトの場合
    //"eslint-config-pirika" それ以外の場合
  ],
  root: true,
};
```

### `.prettierrc.js` の設定

```js
const prettierConfig = require("eslint-config-pirika/prettier-config");

module.exports = {
  ...prettierConfig,
};
```

## 設定内容

### ESLint

ベースは`eslint-config-airbnb`とし、以下の点を変更。

- `no-use-before-define`
    - 定義より前に使用できない (@typescript-eslint 側を使用)
- `@typescript-eslint/explicit-member-accessibility`
    - クラスの public/private は必ず書く
- `lines-between-class-members`
    - クラスメンバ間の空行は入れる。ただしフィールド宣言等1行のときは入れない。
- `no-void`
    - 式文の最初に書くものだけ許可(Promiseの戻りを取らない呼び出し時に使用する)
- `import/extensions`
    - js/jsx/ts/tsx 以外はimportに拡張子が必要(svg等)
- `react/jsx-filename-extension`
    - js/tsでJSXを書いてはいけない
- `react/react-in-jsx-scope`
    - JSXで import React from "react" を書かなくてもいい
- `prefer-arrow/prefer-arrow-functions`
    - なるべくアロー式での関数を書く
- `react/prop-types`, `react/require-default-props`
    - PropTypesは使用しない(TypeScriptで保証されるから)
- `react/function-component-definition`
    - namedComponents, unnamedComponentsともに関数式、アロー式を許容

### Prettier

- `trailingComma`
   - 末尾カンマを常に付ける
- `printWidth`
  - 行の最大桁数は120文字 (長めのidentifierを使用する場合のため)


## LICENSE

MIT