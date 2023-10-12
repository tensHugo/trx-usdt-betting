trx哈希竞猜系统是一套基于波场（tron）开发的虚拟货币USDT、TRX竞猜系统，用户只需要向指定的虚拟货币钱包地址转账即可完成大小竞猜、单双竞猜的玩法。系统完全利用区块链的转账信息来确定竞猜结果，竞猜结果完全公开、公正，无法人工干预。

## 主要特性

* 基于`tron`波场开放API开发
  * 基于波场（tron）官方api开发，无需第三方区块浏览器监控，无任何费用
  * 区块交易信息毫秒级响应，比第三方区块浏览器的数据更快人一步
* 系统自动兑奖
  * 系统每2-3秒刷新一次最新的区块，实时监控区块交易信息
  * 监控到交易信息后，系统自动兑奖（如中奖，自动转账给制定地址）
  * 兑奖失败，自动生成待转账事件
* 完善的权限控制
  * 基于`FastAdmin`、`Thinkphp`开发
  * 拥有完善的权限控制，可创建多个管理员，按需分配后台权限
* 系统内置了USDT<=>TRX 自动兑换
* 完善的USDT、TRX交易查询系统
* 系统支持竞猜网页、哈希交易查询网页、USDT<=>TRX 自动兑换网页 独立域名部署
* 高度集成了Telegram机器人
  * 自定义机器人命令
  * 任意用户都可以添加钱包地址监控
  * 钱包地址交易实时监控，并通过机器人通知
  * 机器人消息群发、一对一对话发送功能

## 安装使用

### 环境要求

PHP >= 7.2 且 <= 7.4 (推荐PHP7.4版本)

MySQL >= 5.7 且 <= 8.0 (需支持innodb引擎)

Apache 或 Nginx

Redis

### 安装教程

trx哈希竞猜系统安装非常友好，只需简单四步即可安装完成，下面以 Linux 宝塔面板 （Linux + NGINX + PHP7.4 + MySQL + Redis）为例。

##### 安装前准备

php开启扩展：`redis`

php禁用函数：`putenv`

composer安装依赖，在网站主目录下，直接运行命令：`composer install`

##### 第一步：新建站点

* 进入宝塔面板，创建一个新的站点，新建站点的数据库，填写项目域名。

##### 第二步：上传解压

- 通过宝塔的文件管理功能，进入站点的文件目录。
- 上传 源码包 并解压到站点的当前目录，比如：/www/wwwroot/demo.trx.co

##### 第三步：配置并安装

* 进入站点配置，设置 `public` 为站点的运行目录（**划重点**），并设置站点的伪静态为 `thinkphp`。
* 访问你的站点域名进行安装，比如：[https://demo.trx.co/install.php](https://demo.trx.co/install.php)
* 安装完成后即可进入后台，比如： [https://demo.trx.co/](https://demo.trx.co/)奇怪的文件名.php
* 至此 trx竞猜系统已经安装完成。
  * 后台地址：~~安装完成后自动生成~~
  * 竞猜首页：http(s)://你的域名/
  * 交易查询页：http(s)://你的域名/hash
  * 代币兑换页：http(s)://你的域名/exchange

##### 第五步：开启tron（波场）网络监控

* 在宝塔软件商店搜索“进程守护管理器”，并安装。建议将进程守护管理器开启首页显示
* 打开宝塔的进程守护管理器，或在软件商店中找到“已安装”，点击“设置”
* 点击“添加守护进程”，按如下填写：
  * 名称：tronBlock（也可以任意填写）
  * 启动用户：root
  * 进程数量：1
  * 启动优先级：999
  * 启动命令：`php think queue:listen --queue TronBlockTask --sleep 0`
  * 进程目录：`/www/wwwroot/你的网站目录`<<--注意替换成你的网站目录
  * 备注：tronBlock（也可以任意填写）

![宝塔进程守护应用](https://raw.githubusercontent.com/tensHugo/img-hugou/master/bt-jincheng-tools.jpg "宝塔进程守护应用")

![添加进程守护](https://raw.githubusercontent.com/tensHugo/img-hugou/master/bt-jinchen-tronBlock.jpg "添加进程守护")

## 在线演示

[https://test2.fsasa.cc/CjrMZcbWXK.php](https://test2.fsasa.cc/CjrMZcbWXK.php/)

用户名：admin

密　码：rootadmin

提　示：演示站数据无法进行修改，请下载源码安装体验全部功能

## 界面截图

#### 前端截图

![竞猜首页](https://raw.githubusercontent.com/tensHugo/img-hugou/master/jingcai-home.jpg "竞猜首页")
![兑换首页](https://raw.githubusercontent.com/tensHugo/img-hugou/master/duihuan-home.jpg "兑换首页")
![哈希查询首页](https://raw.githubusercontent.com/tensHugo/img-hugou/master/hash-hmoe.jpg "哈希查询首页")
![哈希查询页](https://raw.githubusercontent.com/tensHugo/img-hugou/master/hash-chaxun.jpg "哈希查询页")

#### 后台截图

![后台首页](https://raw.githubusercontent.com/tensHugo/img-hugou/master/admin-home.jpg "后台首页")
![后台设置](https://raw.githubusercontent.com/tensHugo/img-hugou/master/admin-config.jpg "后台设置")
![后台机器人设置](https://raw.githubusercontent.com/tensHugo/img-hugou/master/admin-tg-config.jpg "后台机器人设置")
![tg消息管理](https://raw.githubusercontent.com/tensHugo/img-hugou/master/admin-tg-message.jpg "tg消息管理")
![波场监控](https://raw.githubusercontent.com/tensHugo/img-hugou/master/admin-tron-jiankong.jpg "波场监控")
![大小转账](https://raw.githubusercontent.com/tensHugo/img-hugou/master/admin-daxiao-dh.jpg "大小转账")
![异常处理](https://raw.githubusercontent.com/tensHugo/img-hugou/master/admin-zhuanzhang.jpg "异常处理")

## 多域名配置

前端页面一共有三个，可实现单独绑定域名。分别为：

* 竞猜首页
* 交易查询页
* 代币兑换页

#### 设置方法

在网站主目录下有一个`.env.back`文件，如果要开启独立域名请将此文件重命名成`.env`并且参照以下格式编辑：

```
[domain]
open = false   #改成true表示开启多域名
main = trx.co  #主域名和后台域名
betting =      #竞猜首页域名
exchange =     #代币兑换页域名
hash =         #交易查询页域名
```

## 特别鸣谢

感谢以下的项目,排名不分先后

FastAdmin：https://www.fastadmin.net

ThinkPHP：http://www.thinkphp.cn

AdminLTE：https://adminlte.io

Bootstrap：http://getbootstrap.com

jQuery：http://jquery.com

Bootstrap-table：https://github.com/wenzhixin/bootstrap-table

Nice-validator: https://validator.niceue.com

SelectPage: https://github.com/TerryZ/SelectPage

Layer: https://layuion.com/layer/

DropzoneJS: https://www.dropzonejs.com
