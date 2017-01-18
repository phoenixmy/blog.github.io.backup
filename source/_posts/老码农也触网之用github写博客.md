----
title: 老码农也触网之用github写博客（一）
date: 2017-01-16 22:30:36
tags: [github, github.io, hexo, mou, github blog]
----

> <div align="left">作为传统软件领域的老码农，早已对博客不太感冒。一次偶然的机会，我发现github.io可以用于搭建个人博客系统，而且由于基于markdown，语法简洁，灵活度大，样式也非常整齐美观，因此本农也决定下海试试这新潮玩意。在网上一番搜索后，确定了hexo + mou + markdown 这个组合来完成我的自建博客系统。</div>




## 需要准备的软件

__先声明一点：本人用的是mac os，因此所有的工具都是基于mac的__

`git` : _brew install git_

这个就不多说了，从github上往下拉代码都是靠着它，当然博客也不例外.

`node` : _brew install node_

给mac上安装node，最新版的node.js的包中已经集成了npm：一款JavaScript的包管理工具，可以使用命令<code>node -v</code>和<code>npm -v</code>来验证node与npm是否安装成功；如果npm没有安装，请使用 _brew install npm_ 命令来单独安装它。

`hexo`： _npm install -g hexo-cli_

现在是重头戏：安装hexo。截止本文发表，[hexo官网文档](https://hexo.io/docs/index.html)推荐的命令是 _npm install -g hexo-cli_ 。

`hexo edit`： _npm install hexo-cli-extras_

hexo自带的命令是不包含hexo edit的，如果你想编辑一篇原来的博客，就会有点麻烦。通过这个hexo的插件，就可以自由编辑所有文章了。具体的使用请看[该插件的官网介绍](https://www.npmjs.com/package/hexo-easy-edit).

`mou` : [下载地址：25.io](http://25.io/mou/) 

这是个mac上的markdown编辑器，网上评价较高，用了一下挺不错的，这是一个所写即所见的编辑器，左侧是文本编辑框，右侧就是实际的显示效果，对于markdown初学者来说确实是十分的方便。推荐！

软件的使用：下载下来后放到/Applications目录下即可。截止目前，该软件版本是0.8.7beta，后面的1.0就要开始收费了。

## hexo的初步使用

_声明：以下部分引用自网络博文“[Hexo安装和配置](http://www.jianshu.com/p/b7886271e21a)”_

#### 配置hexo编辑环境

<code>
$ hexo init 'folder name'
$ cd 'folder name'
$ npm install
</code>

#### hexo的基本命令

##### hexo的使用
<pre><code>
hexo init xxx  #执行init命令初始化到你指定的xxx目录
cd xxx
npm install    #install before start blogging
hexo generate       #自动根据当前目录下文件,生成静态网页
hexo server    #运行本地服务 网址 http://localhost:4000/
</code></pre>

##### 创建新的博客文章

<pre><code>
hexo new "postName"  #新建博文,其中postName是博文题目
</code></pre>

##### 文件自动生成格式
<pre><code>
title: "It Starts with iGaze: Visual Attention Driven Networkingwith Smart Glasses"  #博文题目
date: 2014-11-21 11:25:38      #生成时间
tags:                    #标签, 多个标签也可以使用格式[tag1, tag2, tag3,...]
- tag1
- tag2
- tag3
categories: [cat1,cat2,cat3]
---
正文, 使用 Markdown 语法书写
</code></pre>

##### 如果不想博文在首页全部显示, 并能出现阅读全文按钮效果, 需要在你想在首页显示的部分下添加

```
`<!--more-->`
```


#### 配置hexo用的编辑器

一般来说，hexo都会使用系统默认指定的代码编辑软件，从环境变量process.env.EDITOR中获取，在我的机器上，这个指代的是xcode的编辑器。可以通过修改脚本 <folder name>/node_modules/hexo-cli-extras/lib/extensions.js：

<pre><code>
var exec = require('child_process').exec;

hexo.on('new', function onNew(post) {
...        
//edit = spawn(editor, [post.path], {stdio: 'inherit'});
//edit.on('exit', process.exit);
exec('open -a "/Applications/Mou.app" ' + post.path);
...
</code></pre>

接下来，如果你再次使用hexo new 或者hexo edit命令来处理文章的时候，就会自动使用mou来进行编辑。



## markdown的简单语法

markdown是一种标记语言，基本的语法规则不超过十种，另外，它还可以用来编辑代码块，脚注，TODO list，表格，流程图，时序图，LaTeX公式等，功能十分强大。

个人感觉[mou主页](http://25.io/mou/)上的那张图就对markdown的基本用法有一个很好的说明：
![mou上的markdown演示效果](http://25.io/mou/img/1.png)


另外还有几篇文章也写的挺好：

* [Markdown基础语法整理](http://www.jianshu.com/p/815788f4b01d)

* [Markdown进阶语法整理](http://www.jianshu.com/p/0b257de21eb5)

* [维基百科上的markdown示例](https://en.wikipedia.org/wiki/Markdown#Example)






> <div align="left">接下来有空的话，我打算继续写写 hexo的主题，hexo在github上的部署，hexo的命令大全，markdown的深入 等话题。</div>





