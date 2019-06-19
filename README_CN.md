# markdown-formatter

[English Document](./README.md)

## 介绍

这是个面向开发者的文档（markdown)开发工具， 为 `markdown` 使用者提供了相对统一的格式。 
## 使用手册

安装完成以后， 你可能需要重新启动你的vscode. 

在任何 `.md` 为后缀的 `markdown` 标准文件中， 都可以使用 `shift+option+f` 快速格式化代码。 

![example.gif](https://raw.githubusercontent.com/sumnow/markdown-formatter/master/images/example.gif)

> 它并不会修复你的 `markdown` 语法错误， 例如作为标题， `#` 后没有加空格， 这是因为在代码中#是一个可用字符， 广泛得用作注释或变量声明。 

## 功能

- `，,。;；！、？：` 这些符号后添加一个空格； 
- `，：；！“”‘’（）？。` , 转换为半角符（可选）; 
- 支持根据上下文将中文后的符号转换为全角符号， 或者将英文后的转化为半角符； 
- `.!?` 后如果是大写的英文字母或者中文会添加一个空格； 
- 反逗号前后空一格， 反逗号内的内容不会被格式化； 
- 标题上下空出一行； 
- 代码块上下空出一行； 
- 表格自动对齐； 
- 为引用上下空出一行； 
- 相邻的空行合并； 
- 依据配置会格式化文章中的代码， 使用 `js-beautify` 工具， 目前只有 `javascript`  `html` 和 `css` 语言； 

### 代码区

    function sayHello() {
      console.log('hello')
    }

 如果 `codeAreaFormat` 为 `true` (默认值）， 会被格式化。 

### 代码块

    ``` lang
    function sayHello() {console.log('hello')}
    ```

1. 如果 `lang` 为 `js` 或者 `javascript` 或者为空， 会按照js语法格式化 

2. 如果 `lang` 为 `html` , 会按照html语法格式化。 
3. 如果 `lang` 为 `css` , 会按照css语法格式化。 
4. 如果你很少写入js代码， *你可以通过配置参数 `formatOpt` 为false来禁止代码块和代码区的自动格式化代码*. 

此外， 还可以通过配置参数 `formatOpt` 更改js格式化规则， 参照[js-beautify](https://github.com/beautify-web/js-beautify).

## 配置

```typescript
// 是否启用格式化
enable = config.get <boolean> ('enable', true); 
// 是否自动格式化代码区
codeAreaFormat = config.get<boolean>('codeAreaFormat', true); 
// 将配置里的全角符号转化为半角符号， 例如 `，：；！“”‘’（）？。` ， 当设置为false的时候， 自动根据上下文转换符号
charactersTurnHalf = config.get<any>('charactersTurnHalf', false); 
// 是否格式化代码或者配置js-beautify(false: 不格式化代码， {}: 配置beautifyjs)
formatOpt = config.get <any> ('formatOpt', {}); 
```

配置 `js-beautify` , 可以参考[这里](https://github.com/beautify-web/js-beautify)

你可以参考我的配置方法：

```js
  "markdownFormatter.codeAreaFormat:": true,
  // "markdownFormatter.charactersTurnHalf": false,
  "markdownFormatter.charactersTurnHalf": "，：；！“”‘’（）？。",
  "markdownFormatter.formatOpt": {
      "indent_size": 2
  }
```

## 开发环境

#### 开发版本

VSCode 版本 1.29.1 (macOS Mojave)

#### 测试版本

VSCode 版本 1.33.1 (macOS Mojave)

## 联系

如果你有任何想法， 请联系我。

如果你知道如何使用前端库格式化其他语言，欢迎告诉我。

email: mydiamervin@gmail.com 或者 [这里](https://github.com/sumnow/markdown-formatter/issues)