# 用 npm 初始化项目，生成package.json
npm init -y

# 项目目录下安装 babel 组件， 防止项目对机器环境产生依赖
# 参考 http://www.ruanyifeng.com/blog/2016/01/babel.html?20170213113809
npm install --save-dev babel-cli babel-preset-env

# 安装完毕后会提示 No repository field.
# 参考 https://blog.csdn.net/harryptter/article/details/76261581
# 如有有项目地址，则在 package.json 中输入下面的配置（末尾配置不含逗号）
"repository": {
   "type": "git",
   "url": "yourgitprojectgiturl.git" //此处填的是你的项目的git url地址  
}
# 如果没有项目地址， 则在 package.json 中输入下面的配置（末尾配置不含逗号）
"private": true

# 项目根目录下创建 .babelrc 文件， 写入如下内容
{
  "presets": ["env"]
}

# src 目录写 es6 js ， dist 目录作为 es5 输出
# 参考 https://www.cnblogs.com/PopularProdigal/p/7081188.html

# 转码结果输出到标准输出
$ babel example.js

# 转码结果写入一个文件
# --out-file 或 -o 参数指定输出文件
$ babel example.js --out-file compiled.js
# 或者
$ babel example.js -o compiled.js

# 整个目录转码
# --out-dir 或 -d 参数指定输出目录
$ babel src --out-dir lib
# 或者
$ babel src -d lib

# -s 参数生成source map文件
$ babel src -d lib -s

# 改写 package.json
# 参考 https://www.cnblogs.com/PopularProdigal/p/7081188.html
"scripts": {
    "build": "babel src/index.js -o dist/index.js"
}
# 或
"scripts": {
    "build": "babel src -d dist"
}

# 用 npm run build 命令打包， 可能用到 webpack
npm run build