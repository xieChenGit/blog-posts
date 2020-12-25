# 前端使用 hexo+github 搭建自己的博客

<a name="Avpo9"></a>
## 使用hexo搭建博客的优点
- 全是静态文件，访问速度快
- 免费方便，不需要话费一分钱就可以搭建自己的个人博客，不需要服务器不需要后台
<a name="Ndwsm"></a>
## 准备工作
在一切开始之前你需要准备：

- 个人GitHub账号
- 安装了Node、npm并且了解相关知识
- 安装了Git（这里仅仅指Window）
<a name="gc6Ya"></a>
## 搭建github博客
<a name="IIxhc"></a>
### 新建仓库
**创建一个和你的用户名相同的仓库，****后面加 .github.io 后缀，必须要同名哦**，不然后面会出现页面404的情况，点击create  respository按钮创建。<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/209060/1605253719178-bd4cf0b3-58e0-4a73-a3fa-d08430d709e5.png#align=left&display=inline&height=730&margin=%5Bobject%20Object%5D&name=image.png&originHeight=730&originWidth=745&size=64999&status=done&style=none&width=745)
<a name="ltRDr"></a>
### 配置SSH Key
为什么要配置这个呢？因为你提交代码的时候肯定要有你的github权限才可以，但是直接使用用户名和密码太不安全了，所以我们使用ssh key来解决本地和服务器连接的问题<br />如何安装Git这里就不展开叙述了，可以自己查阅资料。<br />Git Bash 后输入
```git
$ cd ~/. ssh #检查本机已存在的ssh密钥
```
如果提示：No such file or directory 说明你是第一次使用git。
```git
ssh-keygen -t rsa -C "邮件地址"
```
这个时候可以看到在磁盘里面生成了私人密钥和公共密钥了<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/209060/1605254642372-d6bf502f-76d8-415a-891b-c2f538448289.png#align=left&display=inline&height=172&margin=%5Bobject%20Object%5D&name=image.png&originHeight=172&originWidth=1118&size=21904&status=done&style=none&width=1118)<br />
<br />找到`.ssh\id_rsa.pub`文件，记事本打开并复制里面的内容，打开你的github主页，进入个人设置 -> SSH and GPG keys -> New SSH key：

![](https://cdn.nlark.com/yuque/0/2020/webp/209060/1605254734884-b9e6e83e-5db2-4d37-8deb-db2def3b668a.webp#align=left&display=inline&height=315&margin=%5Bobject%20Object%5D&originHeight=315&originWidth=1080&size=0&status=done&style=none&width=1080)
<a name="jmqTB"></a>
## 使用hexo写博客
<a name="dZiSg"></a>
### hexo的介绍
hexo是一个简单、快速、强大的基于GitHub Pages的博库发布工具，支持Markdown格式，，有众多优秀的主题和插件。<br />官网：[http://hexo.io/](http://hexo.io/)<br />github：[https://github.com/hexojs/hexo](https://github.com/hexojs/hexo)
<a name="jenQI"></a>
### 安装node和npm
hexo是基于node.js，本地需要安装node 和 npm，安装步骤就不多说了，可以自己查阅资料。<br />可以查看一下本地是否有版本号，有的话就是安装成功的。<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/209060/1605255178429-3f8197d5-55e1-4f22-95b1-b8fcbd94e7bb.png#align=left&display=inline&height=135&margin=%5Bobject%20Object%5D&name=image.png&originHeight=135&originWidth=271&size=3572&status=done&style=none&width=271)<br />全局安装 hexo
```git
$ npm install -g hexo
```
<a name="aIZ23"></a>
### 初始化一个项目
在电脑的某个地方新建一个名为hexo的文件夹（名字可以随便取），比如我的是`F:\hexo`，由于这个文件夹将来就作为你存放代码的地方，所以最好不要随便放。
```git
$ hexo init blog
```
然后你就会看到D盘里面生成了一个名字为blog的文件夹<br />进入到文件夹，安装依赖文件
```git
$ cd  blog
$ npm  install
```
在控制台输入命令就可以看到博客的页面了
```git
$ hexo server
```
<a name="vFPqD"></a>
## 修改主题
1、博客主题的安装<br />主题这一块可以选择自己喜欢的，以下是以一个Anisina主题为例，这里有很多主题可以选择：传送门[https://hexo.io/themes/](https://hexo.io/themes/)。比如选一个主题：[https://github.com/haojen/hexo-theme-Anisina](https://github.com/haojen/hexo-theme-Anisina)，打开链接，进入到GitHub里面，有详细的安装教程。<br />2、安装主题命令输入
```git
$ git clone https://github.com/Haojen/hexo-theme-Anisina.git themes/Anisina
```
![](https://cdn.nlark.com/yuque/0/2020/webp/209060/1605255649898-eaf1f9f1-5953-4178-8d52-0360c76d60ab.webp#align=left&display=inline&height=249&margin=%5Bobject%20Object%5D&originHeight=249&originWidth=1080&size=0&status=done&style=none&width=1080)<br />
<br />2、打开`_config.yml`文件夹，更改主题名字![](https://cdn.nlark.com/yuque/0/2020/webp/209060/1605255699410-1f9f2340-2edc-4d3d-bfdc-873444caac45.webp#align=left&display=inline&height=638&margin=%5Bobject%20Object%5D&originHeight=638&originWidth=977&size=0&status=done&style=none&width=977)<br />
<br />4、再次启动，就可以看到更换的主题了
<a name="ishqd"></a>
## 部署到 github
1、在配置文件中填写仓库地址<br />在项目    里面找到 _config.yml文件，找到deploy字段，把下面的代码放进去，填写你自己的仓库地址<br />![code.png](https://cdn.nlark.com/yuque/0/2020/png/209060/1605256427534-fc5a10b7-f7cd-4ce0-8644-0be53e4b0f2d.png#align=left&display=inline&height=388&margin=%5Bobject%20Object%5D&name=code.png&originHeight=388&originWidth=1216&size=56261&status=done&style=none&width=1216)<br />2、安装一个推送工具，将本地项目推到仓库上
```git
$ npm install hexo-deployer-git --save
```
3、然后执行命令<br />清除了你之前生成的东西，也可以不加。
```git
$ hexo clean
```
4、hexo generate  生成静态文件，可以用 hexo g缩写
```git
$ hexo  g
```
![](https://cdn.nlark.com/yuque/0/2020/webp/209060/1605256561891-e751ae41-6ac4-4ca9-9e1b-56564318b286.webp#align=left&display=inline&height=304&margin=%5Bobject%20Object%5D&originHeight=542&originWidth=1080&size=0&status=done&style=none&width=605)![](https://cdn.nlark.com/yuque/0/2020/webp/209060/1605256580541-1f98eb43-d6a9-4253-b862-47cd546fd896.webp#align=left&display=inline&height=463&margin=%5Bobject%20Object%5D&originHeight=463&originWidth=257&size=0&status=done&style=none&width=257)<br />可以看到在目录里面生成了一个静态的文件，生成好的public文件夹就直接当成静态网站进行部署即可。<br />5、部署
```git
$ hexo deploy
```
6、查看仓库，已经将项目放到仓库里面了。<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/209060/1605257055568-0b64d2f2-51a2-43d9-93ec-7a7530c43a5d.png#align=left&display=inline&height=618&margin=%5Bobject%20Object%5D&name=image.png&originHeight=618&originWidth=1238&size=69774&status=done&style=none&width=1238)<br />这个时候就可以访问了，已经把静态文件都托管在GitHub了，查看分配的地址：[https://xiechengit.github.io/](https://xiechengit.github.io/)
<a name="xb8Kh"></a>
## 写博客
定位到我们的hexo目录，输入
```git
$ hexo new 'newpapername'
```
hexo会帮我们在`_posts`下生成相关md文件，我们只需要打开这个文件就可以开始写博客了，默认生成如下内容：<br />![code.png](https://cdn.nlark.com/yuque/0/2020/png/209060/1605258439873-7f64d289-4c72-4160-96c6-82051b69f530.png#align=left&display=inline&height=352&margin=%5Bobject%20Object%5D&name=code.png&originHeight=352&originWidth=1216&size=39229&status=done&style=none&width=1216)<br />当然你也可以直接自己新建md文件，用这个命令的好处是帮我们自动生成了时间。<br />当你写完的时候，再输入命令
```git
$ hexo clean
$ hexo g
$ hexo d
```
就可以看到新增的自己的文章了.
<a name="RzW2S"></a>
### 如何让博文列表不显示全部内容
默认情况下，生成的博文目录会显示全部的文章内容，如何设置文章摘要的长度呢？<br />答案是在合适的位置加上<!--more-->即可，例如：<br />![code.png](https://cdn.nlark.com/yuque/0/2020/png/209060/1605259416487-c53f369b-0c3b-47e7-b8ba-473da8b1ee7a.png#align=left&display=inline&height=345&margin=%5Bobject%20Object%5D&name=code.png&originHeight=682&originWidth=1216&size=88490&status=done&style=none&width=615)
<a name="2ZmN2"></a>
## hexo 常用的命令
常见命令
```json
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
```
缩写
```json
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```
组合命令
```json
hexo s -g #生成并本地预览
hexo d -g #生成并上传
```
<a name="57Ivd"></a>
## 感谢

- [https://mp.weixin.qq.com/s/bu6dRiUpzXGvGoEffqwBUg](https://mp.weixin.qq.com/s/bu6dRiUpzXGvGoEffqwBUg)
- [https://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html#%E5%B8%B8%E7%94%A8hexo%E5%91%BD%E4%BB%A4](https://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html#%E5%B8%B8%E7%94%A8hexo%E5%91%BD%E4%BB%A4)
