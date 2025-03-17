## 安装

### 1.主控服务器验证
web目录为验证文件，请自行搭建

```shell
vi /etc/hosts
```
添加一行
```
0.0.0.0  auth.cdnfly.cn monitor.cdnfly.cn
```
0.0.0.0改成自己搭建的验证服务器的IP

### 2.主控安装 v5.1.13
```shell
curl -fsSL https://raw.githubusercontent.com/okcdn100/cdn/main/cdnfly/v5.1.13/master/master.sh -o master.sh && chmod +x master.sh && ./master.sh --es-dir /home/es
```

### 2.主控安装 v5.1.11
```shell
curl -fsSL https://raw.githubusercontent.com/okcdn100/cdn/main/master.sh -o master.sh && chmod +x master.sh && ./master.sh --es-dir /home/es
```

### 3.节点安装
```shell
curl -m 5 https://raw.githubusercontent.com/okcdn100/cdn/main/cdnfly/v5.1.13/agent/agent.sh -o agent.sh
```

修改为你自身安装节点,或使用默认的github节点安装
/opt/cdnfly/master/panel/src/views/system/update/index.html

主控登录地址为: http://主控IP/
管理员账号和密码： admin/cdnfly
普通用户账号和密码： jason/cdnfly

## 服务器配置要求

### 主控
1.内存 - 因为主控安装有Elasticsearch，推荐16G及以上，如果网站访问量比较小，8G也行，至少4G。
2.硬盘 - 建议固态硬盘, 同样考虑访问日志大小，推荐100G及以上，量小的话都可以。
3.CPU - CPU至少2核
4.开放80 88 9200端口

### 节点
1.内存 - 至少2G及以上
2.硬盘 - 根据网站缓存的大小配置
3.CPU - Nginx主要是跑CPU，所以要想访问性能好，CPU尽量好点。
4.开放80 443 5000端口

### 系统
支持Centos-7.6

## 官方最新公告
尊敬的cdnfly用户:
目前发现登录安全漏洞，需要及时按照如下方法来临时修复。找一个只有你知道的域名,这个域名用于管理员登录。
路径为:系统管理--->系统设置--->用户相关，限制管理员只能从此域名登录
