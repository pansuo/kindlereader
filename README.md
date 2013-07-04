# Kindlereader

一个定时将RSS/ATOM feed发送至kindle的工具

其中master分支自改为不再依赖Google Reader以来，由[WilliamGates](https://github.com/williamgateszhao)开发

**2013年7月1日Google Reader关闭服务之后GR和gae分支版本将无法使用**

* [master](https://github.com/williamgateszhao/kindlereader/tree/NoGR) 分支为单用户版(基于python), 不依赖于Google Reader的API，从config.ini文件读取Feed地址并获取数据，运行于 Linux, Mac OSX, Windows
* [GR](https://github.com/jiedan/kindlereader/tree/GR) 分支为单用户版(基于python), 运行于 Linux, Mac OSX, Windows，从Google reader获取Rss更新
* [gae](https://github.com/jiedan/kindlereader/tree/gae) 分支为运行于 Google app engine 的多用户版，从Google reader获取Rss更新, demo: [http://www.mydogear.com](http://www.mydogear.com)


## 使用说明

* 详细使用说明请看[这里](http://blog.williamgates.net/2013/04/kindle-reader-without-google-reader/)

## 简要使用说明（Master/GR分支）
* 安装 Python (建议版本2.7), 大多Liunx和OSX已内置Python
* 修改 config.sample.ini 为 config.ini 并按说明修改其中内容
* 下载并拷贝 kindlegen 到 kindlereader.py 所在目录，并添加可执行权限
* 在终端或命令符内运行 ```python kindlereader.py```

## 对Windows用户的特别说明（Master/GR分支）
* kindlereader.exe 运行不需要安装 Python 环境, 将 kindlereader.exe 和 kindlegen.exe 及 config.ini 放在同一目录内，运行 kindlereader.exe 即可
* 暂时仅测试了Win7平台，不能保证支持WinXP及更早版本
* WinXP用户必须安装[Microsoft Visual C++ 2008 Redistributable Package](http://www.microsoft.com/en-us/download/details.aspx?id=29)

## 参考

* python: [http://www.python.org/](http://www.python.org/)
* py2exe: [http://www.py2exe.org/](http://www.py2exe.org/)
* feedparser: [http://pythonhosted.org/feedparser/](http://pythonhosted.org/feedparser/)
* Kindlestrip: [Kindlestrip](http://www.mobileread.com/forums/showthread.php?t=96903)
* Kindlegen下载地址: [KindleGen](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000765211)

## 许可

Kindlereader is Licensed under the MIT license: [http://www.opensource.org/licenses/mit-license.php](http://www.opensource.org/licenses/mit-license.php)

## Master分支改为不依赖Google Reader（即原来的NoGR分支）以来更新历史

* 0.6.5 修正一个当rss中author为空时的隐蔽错误；修正运行目录不能含有空格的错误；修改模板，在正文界面显示来源和作者；停止为多用户版进一步重构，代码与多用户版开始区分
* 0.6.4 修正win下的路径错误；修正目录页的内容摘要（过滤html标签）；更换BeautifulSoup版本
* 0.6.3 新增时区选项，所有可见的日期显示均根据用户选择的时区（默认为+8）；新增灰度图选项，在生成mobi前将图片转为灰度图，减小文件体积（默认关闭）；允许用户选择是否启用kindlestrip
* 0.6.2 修改mobi文件标题，现在periodical格式在原生系统能自动归档了（但两个文件为同一天的，会将较新的文件归档，目前无法解决）
* 0.6.1 修复一些问题；尝试处理一些不合规范的时间信息；在所有文章信息中均使用utc时间
* 0.6.0 对feed读取也采取了多线程，大幅度提高速度；重构代码，为开发多用户版做准备
* 0.4.9 增加强制全文输出的功能，使用[fivefilters.org](http://fivefilters.org/)，为了避开该站点免费用户每次只能输出3篇文章的限制，尝试将每篇文章单独发给该站点进行解析
* 0.4.8 不再需要安装feedparser库，Python 2.7环境可以直接使用本程序
* 0.4.7 优化feed读取和图片下载流程，下载失败自动进行重试；修复了对不提供发布时间的RSS格式支持
* 0.4.6 修复了对图片URL中含有非ASCII字符的支持，并加强了下载图片的效率和适应性
* 0.4.5 修复了对不提供author或content节点的RSS格式支持
* 0.4.4 引入[Kindlestrip](http://www.mobileread.com/forums/showthread.php?t=96903)，大幅度压缩了生成mobi文件的大小（一般小于原先的50%）;打包了exe文件，使得NoGR分支可以在windows不依赖Python环境运行，对普通用户更加友好
* 0.4.3 修复了不会自动退出的BUG;修复了对"/"结尾Feed地址处理的BUG
* 0.4.2 修复了某些feed地址必须以"/"结尾或反之所导致的问题，对feed是否读取成功进行判断
* 0.4.1 增加限制最旧文章时间的功能;修改了日期格式
* 0.4.0 it works
