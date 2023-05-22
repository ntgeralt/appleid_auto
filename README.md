20230522 白话版APPID自动解锁
首先感谢原项目。
# 基本简介
“以全新方式管理你的 Apple ID” —— 这是一款基于密保问题的自动化 Apple ID 检测&解锁程序。
前端用于管理账号，支持添加多个账号，并提供展示账号页面；
支持创建包含多个账号的分享页面，并可以为分享页面设置密码。
后端定时检测账号是否被锁定，若被锁定或开启二步验证则自动解锁，修改密码并向API回报密码。
登录Apple ID并自动删除Apple ID中的设备。
启用代理池和Selenium集群，提高解锁成功率，防止风控。

# 项目特点
- 多用户使用，权限控制
- 多账号管理
- 账号分享页，支持设置密码、有效期、自定义HTML内容
- 自动解锁与关闭二步验证
- 自动/定时修改密码
- 自动删除Apple ID中的设备
- 代理池与Selenium集群，提高解锁成功率
- 允许手动触发解锁
- ……

# 使用教程

腾讯香港1H1G debian11 ，前后端一体。宝塔PHP7.4 +MYSQL5.6 新建一个页面例如appid.xxxxx.com

cd /www/wwwroot/appid.xxxxx.com

git rclone https://github.com/ntgeralt/appleid_auto.git

然后把文件剪贴到/www/wwwroot/appid.xxxxx.com根目录

修改配置文件.example.env名字改为.env

跟这里，一路做下去

https://appleid-auto.gitbook.io/doc_zhcn/install/qian-duan-wang-zhan-an-zhuang

有两个需要注意的。一个是
API_KEY = 123456我们改成随机7798hg98H7GT6之类。为后端对接前端用

一个是
WEBDRIVER = http://localhost:4444 必须要改成后端获得的IP地址（看倒数第二图）。

最后一步在网站根目录下执行指令，创建管理员账户

php think register 用户名 密码


之后一键部署后端，这里要注意

#一键脚本

bash <(curl -Ls https://raw.githubusercontent.com/pplulee/appleid_auto/backend/backend/install_unblocker.sh)

先输入域名appid.xxxxx.com

然后输入API_KEY之前设置的7798hg98H7GT6

然后一路按Y不要回车缺省。

![536458fcb3c983da2394088878e8fa0](https://github.com/ntgeralt/appleid_auto/assets/8230651/404995e7-445e-411e-af28-f96b8d710c54)

最后进入ip:64000看获得的ip

![55b5495ea025c5102605b87b97dca5d](https://github.com/ntgeralt/appleid_auto/assets/8230651/b53070d3-f192-4e30-8042-6cc79beda3b0)

复制你的，例如上图http://172.17.0.3:4444

改.env WEBDRIVER = http://172.17.0.3:4444 （如果前后端分开，则填入后端域名or ip）


完工。进入appid.xxxxx.com添加个appid看webdrive正不正常即可。![c0ebaa7eb04bd5e4012e3b448b8ffff](https://github.com/ntgeralt/appleid_auto/assets/8230651/db8f1352-5ef4-4af0-a112-dd35d76e6750)
