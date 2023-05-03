# 待办

1. 安装docker
2. 安装宝塔面板
3. 安装可道云
4. 配置内网穿透cpolar
5. 安装python环境（机器学习等）
6. 挂载硬盘

# 树莓派开关机

## 查看树莓派IP：

记下MAC，在同网段的PC上运行 arp  -a 命令，查看MAC对应的IP即可（最简）

MAC：e4-5f-01-b9-cb-cf

关机：sudo shutdown -h now

## 设置固定IP：



# 用硬盘作为系统盘

安装刷系统：https://blog.csdn.net/lpwmm/article/details/110955531

https://www.tomshardware.com/how-to/boot-raspberry-pi-4-usb



## 初始化和挂载新硬盘：

https://support.huaweicloud.com/qs-evs/evs_01_0034.html

执行命令：

1. **lsblk**查看新硬盘信息

   root@raspberrypi:~# lsblk
   NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
   **sda           8:0    0  1.8T  0 disk**** 
   **└─sda1        8:1    0   16M  0 part**** 
   mmcblk0     179:0    0 29.7G  0 disk 
   ├─mmcblk0p1 179:1    0  256M  0 part /boot
   └─mmcblk0p2 179:2    0 29.5G  0 part /

2. 新增硬盘 parted /dev/sda    ，输入“p”，按“Enter”，查看当前磁盘分区形式

3.  *磁盘分区形式***mklabel gpt**      输入“p”，按“Enter”，查看当前磁盘分区形式

4. 输入“unit s”，按“Enter”，设置磁盘的计量单位为磁柱

5. **mkpart test 2048s 100%**     输入“p”，按“Enter”，查看当前磁盘分区形式

6. 输入“q”，按“Enter”，退出parted分区工具



1. **执行以mkfs** **-t** *文件系统格式* **/dev/sda1**  命令，将新建分区文件系统设为系统所需格式                               如：**mkfs -t ext4 /dev/sda1**

2. 执行以下命令，新建挂载目录。

   **mkdir** *挂载目录*

3. **mount** *磁盘分区* *挂载目录*       如：**mount /dev/sda1  /mnt/home**

设置开机自动挂载磁盘分区：略，具体看上面的帖子链接









# 安装docker

参考：https://zhuanlan.zhihu.com/p/435808727



# 宝塔面板安装：

参考：https://www.bt.cn/new/download.html

wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && sudo bash install.sh ed8484bec



启停命令：（root用户执行）

1、启动宝塔面板服务：（启动后，就可以访问宝塔管理面板） /etc/init.d/bt start

2、停止宝塔面板服务： /etc/init.d/bt stop

3、重启宝塔面板服务： /etc/init.d/bt restart

==================================================================
外网面板地址: http://163.142.201.230:41682/a789ff33
内网面板地址: http://192.168.0.106:41682/a789ff33
|-用户名: ttb9ktfy
|-新密码: Gmcc12#$

**执行bt进入菜单模式：**

**root@raspberrypi:/www/server/panel# bt**
===============宝塔面板命令行==================
(1) 重启面板服务           (8) 改面板端口
(2) 停止面板服务           (9) 清除面板缓存
(3) 启动面板服务           (10) 清除登录限制
(4) 重载面板服务
(5) 修改面板密码           (12) 取消域名绑定限制
(6) 修改面板用户名         (13) 取消IP访问限制
(7) 强制修改MySQL密码      (14) 查看面板默认信息
(22) 显示面板错误日志      (15) 清理系统垃圾
(23) 关闭BasicAuth认证     (16) 修复面板(检查错误并更新面板文件到最新版)
(24) 关闭动态口令认证          (17) 设置日志切割是否压缩
(25) 设置是否保存文件历史副本  (18) 设置是否自动备份面板
(0) 取消                   (29) 取消访问设备验证



## 问题：

1. 按照提示的账号和密码，无法正常登录页面

2. 到宝塔的python环境，补充缺失的包：

   root用户，进入/www/server/panel/pyenv/bin

   执行./pip install requests -i https://pypi.tuna.tsinghua.edu.cn/simple/

   执行./pip3 install gevent -i https://pypi.tuna.tsinghua.edu.cn/simple/

   执行./pip install psutil -i https://pypi.tuna.tsinghua.edu.cn/simple/

   python安装源：

   清华大学：https://pypi.tuna.tsinghua.edu.cn/simple/

   阿里云：http://mirrors.aliyun.com/pypi/simple/

   豆瓣：[http://pypi.douban.com/simple/](http://pypi.doubanio.com/simple/)

   

# 可道云安装

数据库：www_orange_com         mPzCW5PpZM

数据库名：**www_orange_com**

用户：**www_orange_com**

密码：**mPzCW5PpZM**

访问站点：http://www.orange.com/index.php



数据库名：**www_orange_kodb**

用户：**www_orange_kodb**

密码：**6fH22W6Smt**

访问站点：http://www.orange.kodbox.com/index.php



数据库名：**www_orange_net**

用户：**www_orange_net**

密码：**5CDrzjfKbW**

访问站点：http://www.orange.net/index.php



访问url:http://192.168.0.106:88/

admin/Gmcc12#$

**外网访问url:http://192.168.194.131:88/**

admin/Gmcc12#$



# WordPress安装

数据库名：**orange_wp_com**

用户：**orange_wp_com**

密码：**FDzZ8ecnsb**

访问站点：http://orange.wp.com/index.php

# 内网穿透

## zerotier

networkid：b15644912ee3be1c



https://blog.csdn.net/m0_61219786/article/details/124788989

*** Success! You are ZeroTier address [ 36192d30ab ]



# 常用命令

要列出系统上安装的所有软件包：sudo apt list --installed

删除已安装的软件：sudo apt-get autoremove --purge softname

修改root密码：passwd root

创建用户组：sudo groupadd 组名

删除用户组：sudo groupdel 组名

创建用户：sudo useradd -m -g 组名 新建用户名





