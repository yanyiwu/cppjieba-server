# CppJieba Server

[![Author](https://img.shields.io/badge/author-@yanyiwu-blue.svg?style=flat)](http://yanyiwu.com/) 
[![License](https://img.shields.io/badge/license-MIT-yellow.svg?style=flat)](http://yanyiwu.mit-license.org)

## 简介

此项目吧，不建议使用。是一些老代码，不舍得扔掉，先放这里吧。

## 用法

### 依赖软件

* `g++ (version >= 4.1 is recommended) or clang++`;
* `cmake (version >= 2.6 is recommended)`;

### 下载和编译

```sh
git clone --depth=10 --branch=master git://github.com/yanyiwu/cppjieba-server.git
cd cppjieba-server
mkdir build
cd build
cmake ..
make
```

## 服务使用

服务默认使用 MixSegment 切词方式，如果想要修改成其他方式，请参考 `src/server.cpp` 源码文件。
将对应的方式的代码行注释去掉，重新编译即可。

### 启动服务

```
./bin/cjserver ../conf/server_example.conf
```

### 客户端请求示例

```
curl "http://127.0.0.1:11200/?key=南京市长江大桥"
```

```
["南京市", "长江大桥"]
```

```
curl "http://127.0.0.1:11200/?key=南京市长江大桥&format=simple"
```

```
南京市 长江大桥
```

默认切词算法是MixSegment切词算法，如果想要使用其他算法切词，可以使用参数method来设置。
示例如下：

```
curl "http://127.0.0.1:11200/?key=南京市长江大桥&format=simple&method=MP"
curl "http://127.0.0.1:11200/?key=南京市长江大桥&format=simple&method=HMM"
curl "http://127.0.0.1:11200/?key=南京市长江大桥&format=simple&method=MIX"
curl "http://127.0.0.1:11200/?key=南京市长江大桥&format=simple&method=FULL"
curl "http://127.0.0.1:11200/?key=南京市长江大桥&format=simple&method=QUERY"
```

用 chrome 浏览器打开也行 ( chrome 设置默认编码是`utf-8`):

同时，也支持HTTP POST模式，使用如下调用:

```
curl -d "南京市长江大桥" "http://127.0.0.1:11200/"
```

返回结果如下：

```
["南京市", "长江大桥"]
```

因为 HTTP GET 请求有长度限制，如果需要请求长文的，请使用POST请求。

### 安装服务(仅限 linux 系统)

如果有需要**安装使用**的，可以按照如下操作：
```
sudo make install
```

### 服务启动和停止(仅限 linux 系统)

```
cd /usr/local/cppjieba-server
./script/cjserver.start
./script/cjserver.stop
```

### 卸载服务(仅限 linux 系统)

```sh
rm -rf /usr/local/cppjieba-server
```

## 客服

+ Email: `i@yanyiwu.com`
+ QQ: 64162451

![image](http://7viirv.com1.z0.glb.clouddn.com/5a7d1b5c0d_yanyiwu_personal_qrcodes.jpg)

## 许可证

MIT http://yanyiwu.mit-license.org

## 作者

- yanyiwu https://github.com/yanyiwu i@yanyiwu.com

[GoJieba]:https://github.com/yanyiwu/gojieba
[CppJieba]:https://github.com/yanyiwu/cppjieba
[jannson]:https://github.com/jannson
[cppjiebapy]:https://github.com/jannson/cppjiebapy
[cppjiebapy_discussion]:https://github.com/yanyiwu/cppjieba/issues/1
[NodeJieba]:https://github.com/yanyiwu/nodejieba
[jiebaR]:https://github.com/qinwf/jiebaR
[simhash]:https://github.com/yanyiwu/simhash
[代码详解]:https://github.com/yanyiwu/cppjieba/wiki/CppJieba%E4%BB%A3%E7%A0%81%E8%AF%A6%E8%A7%A3
[libcppjieba]:https://github.com/yanyiwu/libcppjieba
[issue25]:https://github.com/yanyiwu/cppjieba/issues/25
[exjieba]:https://github.com/falood/exjieba
[KeywordServer]:https://github.com/yanyiwu/keyword_server
[ngx_http_cppjieba_module]:https://github.com/yanyiwu/ngx_http_cppjieba_module
[dict.367W.utf8.tar.gz]:http://pan.baidu.com/s/1o6A0BWY
[cjieba]:http://github.com/yanyiwu/cjieba
[jieba_rb]:https://github.com/altkatz/jieba_rb
[iosjieba]:https://github.com/yanyiwu/iosjieba
[Jieba中文分词系列性能评测]:http://yanyiwu.com/work/2015/06/14/jieba-series-performance-test.html
[pg_jieba]:https://github.com/jaiminpan/pg_jieba
[gitbook-plugin-search-pro]:https://plugins.gitbook.com/plugin/search-pro
