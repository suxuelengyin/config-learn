## 按照官网上的流程所遇到的疑问
### <font color="rgb(24, 144,255)">为什么要安装lodash依赖？</font> 
lodash是一个js工具库，里面包含了大量的Javascript常用的函数，根据官网的介绍，lodash是一个JavaScript的实用工具库,表现一致性，模块化，高性能，以及可扩展。  
官网地址：[lodash英文](https://lodash.com/)；  
中文文档：[lodash中文](http://lodash.think2011.net/)，仅供参考。  
lodash不同于jq库，它主打的并不是dom，而是**数据结构**，**数值计算**等非dom操作。  
### --save和--dev-save的区别?
--save安装的依赖将会被打包进入静态文件，即项目启动需要的依赖。  
--dev-save是开发者为了方便自己进行开发安装的依赖，如测试工具，最后不会被使用。

***
### 为什么可以直接使用ES6的import和export？  
 webpack能够提供开箱即用般的支持。事实上，webpack在幕后会将代码“转译”，以便旧版本浏览器可以执行。更多支持请查看[模块语法](https://www.webpackjs.com/api/module-methods/)。如果你想要使用ES6+其他语法，你仍然需要安装babel。  
 你可能了解，es6的模块化，输出的是值的引用。但是在 webpack 中，你只是用了es6的`style`，而不是真的就是es6，打包后的模块实现，输出的是值的拷贝，务必注意！
 ***
 ### `npm run build`为何要加`run`关键字？
 有4个可以简写的命令：  
 1. `npm start === npm run start`
 2. `npm stop === npm run stop`
 3. `npm test === npm run test`
 4. `npm restart === npm run stop && npm run restart && npm run start`  

其他命令均需要添加run。
***
### style-loader和css-loader
**loader加载的顺序是从右往左的**。css-loader是将css文件以字符串形式解析，解析`@import`等less语法。style-loader是将css样式，生成`<style>`标签，并将其插入到head中。这两个往往是配套出现的，加载顺序必须是先使用css-loader解析，再使用style-loader插入文档，所以顺序一定是`['style-loader', 'css-loader']`。详细文档均在[webpack loaders](https://www.webpackjs.com/loaders/css-loader/)
***
### HtmlWebpackPlugin插件
`HtmlWebpackPlugin`简化了HTML文件的创建，以便为你的webpack包提供服务。用法：
`plugins: [new HtmlWebpackPlugin()]`,这会根据webpack的配置自动生成html文件和打包后的js文件,css文件d等。该构造函数接收一个options参数，可以修改html的文件名，titled等配置。详细文档请移步[html-webpack-plugin](https://github.com/jantimon/html-webpack-plugin)
****
### clean-webpack-plugin插件
通常，在每次构建前清理`/dist`文件夹，是比较推荐的做法，因此只会生成用到的文件。该插件可以自动清理指定输出文件夹。详细用法[ clean-webpack-plugin](https://www.npmjs.com/package/clean-webpack-plugin)。
****
### mainfest
管理所有模块的交互。研究webpack原理可以了解一下。
****
### source map
当 webpack 打包源代码时，可能会很难追踪到错误和警告在源代码中的原始位置。为了更容易地追踪错误和警告，JavaScript 提供了source map功能，将编译后的代码映射回原始源代码。source map有多种不同的选项，具体请看[source map](https://www.webpackjs.com/configuration/devtool/)  
****
### 自动构建和重启
webpack 中有几个不同的选项，可以帮助你在代码发生变化后自动编译代码：
1. webpack's Watch Mode
2. webpack-dev-server
3. webpack-dev-middleware  

观察模式只能自动监听文件改变然后重新构建。`webpack-dev-server`提供了一个简单的web服务器，并且能够实时重新加载(live reloading)。`webpack-dev-middleware`是一个容器(wrapper)，它可以把webpack处理后的文件传递给一个服务器(server)。   
多数情况下使用的是`webpack-dev-server`  
### 模块热替换
前端模块化之后，每一个文件都是一个模块或者功能，由 webpack 构建的应用，可以启用HRM模块热替换的功能，在`webpack-dev-server`启动时热更新模块，而不用重新构建，这是我们最常用的功能，每一次文件变动，都将最优化地启动热更新，方便我们调试开发。


