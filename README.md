# vue2-admin-brand
基于vue2/element-ui搭建的后台admin基础框架，导航栏打开页为面包屑，基础功能详见README

代码说明：copy源码后，只需在根目录下cmd执行命令 npm install 安装依赖包即可跑起来;


功能说明：
----
    标准的文件构建目录-
    头部和脚部共用-
    登录控制-
    非登录端与登录端view主组件区分-
    axios封装成ajax的数据请求方式，支持跨域-
    语言国际化-
    登录密码加密-
    sass工具快捷写css-
    阿里巴巴的iconfont支持-
    vue-animate动画效果支持-
    mock模拟数据-
    element-ui组件引入-



框架应用技术栈：
----
    框架：vue2-
    搭建工具：vue-cli/npm/webpack/node-
    UI：element-ui-
    基础库：vuex/axios/vue-router-
    工具库：mock/vue-i18n/vue-animate/crypto-
    其它资源：es6/sass/iconfont/babel-polyfill-
    (es6自带，iconfont通过文件引入，与element-ui兼容，其他库都需npm安装，并写入依赖。)-

目录结构说明：
----
    ├── build                      // 构建相关
    ├── config                     // 配置相关
    ├── src                        // 源代码
    │   ├── api                    // 所有请求
    │   ├── axios                  // 用来封装axios
    │   ├── assets                 // 主题 字体等静态资源
    │   ├── components             // 全局公用组件
    │   ├── directive              // 全局指令
    │   ├── filtres                // 全局 filter
    │   ├── icons                  // 项目所有 svg icons
    │   ├── lang                   // 国际化 language
    │   ├── mock                   // 项目mock 模拟数据
    │   ├── router                 // 路由
    │   ├── store                  // 全局 store管理
    │   ├── styles                 // 全局样式
    │   ├── utils                  // 全局公用方法
    │   ├── vendor                 // 公用vendor
    │   ├── views                   // view
    │   ├── App.vue                // 入口页面
    │   ├── main.js                // 入口 加载组件 初始化等
    │   ├── menu.js                // 配置菜单
    │   ├── permission.js          // 权限管理
    │   └── mock.js                // mockjs文件
    ├── static                     // 第三方不打包资源
    │   └── Tinymce                // 富文本
    ├── .babelrc                   // babel-loader 配置
    ├── eslintrc.js                // eslint 配置项
    ├── .gitignore                 // git 忽略项
    ├── favicon.ico                // favicon图标
    ├── index.html                 // html模板
    └── package.json               // package.json

    build 文件夹: 里面是对 webpack 开发和打包的相关设置，包括入口文件、输出文件、使用的模块等；
    config 文件夹: 主要是指定开发和打包中的静态资源路径、要压缩的文件类型、开发使用的端口号、开发使用虚拟服务器跨域请求 api 等。
    node_modules: 项目的依赖库；
    src 文件夹： 我们主要操作的地方，组件的增加修改等都在这个文件夹里操作，下文会有详细介绍；
    static 文件夹: 静态资源文件夹，放置不会变动的资源，直接被复制到最终的打包目录（默认是dist/static）下；
    .babelrc: 使用 babel 的配置文件，用来设置转码规则和插件；
    .editorconfig: 代码的规范文件，规定使用空格或 tab 缩进，缩进的长度是两位还是四位之类的代码风格，使用的话需要在编辑器里下载对应的插件；
    .eslintignore: 指定 eslint 忽略的文件；
    .eslintrc: 配置 eslint 的检测规则，强制按照规则书写代码；
    .gitignore: 指定 git 忽略的文件，所有 git 操作均不会对其生效；
    .postcssrc: 指定使用的 css 预编译器，里面默认配置了 autoprefixer ，自动补全浏览器前缀；
    favicon.ico: 浏览器标签页 title 旁边的小图标，这是需要我们自己粘贴过来的；
    index.html: 首页文件，项目运行的时候，会自动将我们在 src 文件夹里生成的组件插入这个文件里；
    LICENSE: 项目声明的 license；
    package-lock.json: 当 node_modules 或 package.json 发生变化时自动生成的文件。这个文件主要功能是确定当前安装的包的依赖，以便后续重新安装的时候生成相同的依赖，而忽略项目开发过程中有些依赖已经发生的更新；
    package.json: 指定项目开发和生成环境中需要使用的依赖库；
    README.md: 相当于是一个备注文件，对项目开发过程中需要注意的地方进行一些说明

    assets: 放置静态资源，包括公共的 css 文件、 js 文件、iconfont 字体文件、img 图片文件 以及其他资源类文件。之所以强调是公共的 css 文件，是因为要在组件的 css 标签里加入 ‘scoped‘ 标记，将其作用范围限制在此组件以及调用它的父级组件中，避免污染全局样式；
    components: 放置通用模块组件。项目里总会有一些复用的组件，例如弹出框、发送手机验证码、图片上传等，将它们作为通用组件，避免重复工作；
    http: 放置与后台 api 相关的文件。这里面有 axios 库的实例配置文件、使用配置的 axios 实例接入 api 获取数据的函数的集合的文件；
    mixins: 放置混合选项的文件。具体来说，相当于是公用函数的集合，在组件中引用时，可以作用于组件而不必书写重复的方法；
    pages: 放置主要页面的组件。例如登录页、用户信息页等。通常是这里的组件本身写入一些结构，再引入通用模块组件，形成完整的页面；
    router: 放置路由设置文件，指定路由对应的组件；
    store: 放置 vuex 需要的状态关联文件，设置公共的 state、mutations 等；
    App.vue: 入口组件，pages 里的组件会被插入此组件中，此组件再插入 index.html 文件里，形成单页面应用；
    main.js: 入口 js 文件，影响全局，作用是引入全局使用的库、公共的样式和方法、设置路由等。


框架搭建步骤：（以下所有命令仅针对win系统）
----
    1，安装node
        从官网下载node文件，安装，win+r,输入cmd回车，输入命令：node -v,出现版本号则成功。（已经自带npm）

        如果npm安装资源慢，可以选择安装安装淘宝镜像：
            npm install -g cnpm --registry= https://registry.npm.taobao.org
            cmd回车输入命令：cnpm -v，如果出现版本号则成功。

    2，安装webpack
        打开命令行工具输入：npm install webpack -g，安装完成输入webpack -v，如果出现相应的版本号则安装成功。

    3,安装vue-cli脚手架
        打开命令行工具输入：npm install vue-cli -g，安装完成之后输入 vue -V（注意这里是大写的“V”），如果出现相应的版本号则安装成功。


    注：(如果不是第一次安装，那么，node、webpack、vue-cli应该都已经安装好，可以跳过以上三步，直接进入第四步。)


    4，初始化vue项目，建立页面模板
        ① cd 目录路径；
        ② 安装vue脚手架输入：vue init webpack name；（name为你的项目名称）
        ③
            $ vue init webpack name --------------------- 这个是那个安装vue脚手架的命令
            This will install Vue 2.x version of the template. ---------------------这里说明将要创建一个vue 2.x版本的项目
            For Vue 1.x use: vue init webpack#xxx name
            ? Project name (name) ---------------------项目名称
            ? Project name name
            ? Project description (A Vue.js project) ---------------------项目描述
            ? Project description A Vue.js project
            ? Author Datura --------------------- 项目创建者
            ? Author Datura
            ? Vue build (Use arrow keys)
            ? Vue build standalone
            ? Install vue-router? (Y/n) --------------------- 是否安装Vue路由，也就是以后是spa（但页面应用需要的模块）
            ? Install vue-router? Yes
            ? Use ESLint to lint your code? (Y/n) n ---------------------是否启用eslint检测规则，这里个人建议选no
            ? Use ESLint to lint your code? No
            ? Setup unit tests with Karma + Mocha? (Y/n)
            ? Setup unit tests with Karma + Mocha? Yes
            ? Setup e2e tests with Nightwatch? (Y/n)
            ? Setup e2e tests with Nightwatch? Yes


        ④ cd 命令进入创建的工程目录，首先cd name（这里是自己建工程的名字）；

        ⑤ 安装项目依赖：npm install，因为自动构建过程中已存在package.json文件，所以这里直接安装依赖就行。不要从国内镜像cnpm安装(会导致后面缺了很多依赖库)，但是但是如果真的安装“个把”小时也没成功那就用：cnpm install 吧

            安装vue路由模块 vue-router
                输入：npm i vue-router -S

            安装http请求模块 axios
                输入：npm i axios -S

            安装状态管理 vuex
                输入：npm i vuex -S

            安装模拟数据模块 mockjs
                输入：npm i mockjs -S

            安装页面ui组件库 element-ui
                输入：npm i element-ui -S

            安装加密模块 crypto
                输入：npm i crypto -S

            安装语言国际化工具 vue-i18n
                输入：npm i vue-i18n -S

            安装动画库 vue2-animate
                输入：npm i vue2-animate -S

            安装ie9以上兼容es6语法的工具 babel-polyfill
                输入： npm i babel-polyfill -S

            安装css拓展语言工具 sass
                输入：npm i sass-loader -S
                //sass-loader依赖于node-sass
                输入：npm i node-sass -S

                如果按照失败，可用淘宝镜像安装

                输入：npm install -g cnpm --registry=https://registry.npm.taobao.org  （安装淘宝镜像）

                输入：cnpm install node-sass  --save （使用淘宝镜像安装node-sass）


        ⑥ 启动项目，输入：npm run dev，或者点击文件 start.bat
        ⑦ 打包项目，输入：npm run build，或者点击文件 product.bat



    5，引入各组件库

            ① 引入vue-router，在main.js中加入：

                import Vue from 'vue'
                import VueRouter from 'vue-router'

                Vue.use(VueRouter)

            ② 引入axois，在main.js中加入：

                import axios from "axios";

                注：与很多第三方模块不同的是，axios不能使用use方法，转而应该进行如下操作
                Vue.prototype.$axios = axios;

                let http = axios.create({
                  baseURL: 'http://localhost:8080/',
                  withCredentials: true,
                  headers: {
                    'Content-Type': 'application/x-www-form-urlencoded;charset=utf-8'
                  },
                  transformRequest: [function (data) {
                    let newData = '';
                    for (let k in data) {
                      if (data.hasOwnProperty(k) === true) {
                        newData += encodeURIComponent(k) + '=' + encodeURIComponent(data[k]) + '&';
                      }
                    }
                    return newData;
                  }]
                });

                function apiAxios(method, url, params, response) {
                  http({
                    method: method,
                    url: url,
                    data: method === 'POST' || method === 'PUT' ? params : null,
                    params: method === 'GET' || method === 'DELETE' ? params : null,
                  }).then(function (res) {
                    response(res);
                  }).catch(function (err) {
                    response(err);
                  })
                }

                export default {
                  get: function (url, params, response) {
                    return apiAxios('GET', url, params, response)
                  },
                  post: function (url, params, response) {
                    return apiAxios('POST', url, params, response)
                  },
                  put: function (url, params, response) {
                    return apiAxios('PUT', url, params, response)
                  },
                  delete: function (url, params, response) {
                    return apiAxios('DELETE', url, params, response)
                  }
                }

                这里的配置了POST、GET、PUT、DELETE方法。并且自动将JSON格式数据转为URL拼接的方式

                同时配置了跨域，不需要的话将withCredentials设置为false即可

                并且设置了默认头部地址为：http://localhost:8080/，这样调用的时候只需写访问方法即可



            ③  引入vuex，在main.js中加入：

                import Vuex from 'vuex'

                Vue.use(Vuex)

                Vuex 依赖 Promise。如果你支持的浏览器并没有实现 Promise (比如 IE)，那么你可以使用一个 polyfill 的库，例如 es6-promise。

                npm i es6-promise -S

                将下列代码添加到你使用 Vuex 之前的一个地方：

                import 'es6-promise/auto'

            ④  引入mockjs：

                ①在src中创建mock文件夹，在里面创建mock.js

                ②入口文件中main.js

                import Mock from './mock/mock'


            ⑤ 引入crypto：

                在使用的组件页面中，引入：import crypto from 'crypto'

            ⑥ 引入vue-i18n，在 main.js 中引入：
                import VueI18n from 'vue-i18n'

                Vue.use(VueI18n)

                创建 zh.js 和en.js 中英文数据文件，里面写入中英文数据


                在mian.js文件中写入：
                const i18n = new VueI18n({
                    locale: 'en',  // 语言标识（可用localStorage实现中英文切换记忆功能）
                    messages: {
                        'zh': require('./common/lang/zh'),
                        'en': require('./common/lang/en')
                    }
                })

                把 i18n 挂载到mian.js中的 vue 根实例上：
                const app = new Vue({
                    router,
                    i18n,
                    ...App
                }).$mount('#app')


            ⑦ 引入vue2-animate，在 main.js 中引入：
                import 'vue2-animate/dist/vue2-animate.min.css';



            ⑧ 引入babel-polyfill，在 main.js 中引入：
                import 'babel-polyfill';

            ⑨ 引入sass，在build文件夹下的webpack.base.conf.js的rules里面添加配置：
                {
                  test: /\.sass$/,
                  loaders: ['style', 'css', 'sass']
                }

