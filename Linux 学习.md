# Linux centos 学习

## 1 常用命令

命令格式：```命令[-选项][参数]```

* 命令名称：==ls 选项[-ald]==

  * -a 显示所有文件，包括隐藏文件

  * -l  详细信息显示

  * -d  查看目录属性

* 文件类型
  * -二进制文件 d 目录 l 软链接
  * 文件r 读 w 写 x 执行

* 命令名称：==mkdir -p[目录名]==

  * 创建新目录

  * -p 递归创建 **可以多目录**
  
* 命令名称：==cd[目录]==

  * cd .. 回到上一级
  
* 命令名称：==pwd==

* 显示当前决定路径 		 

* 命令名称：==rmdir[目录名]==
  
  * 删除空目录
  
* 命令名称：rm[名称]

    * -f 强制删除（不询问）
    * -rf 删除目录

* 命令名称：```cp -rp[原文件或目录][目标目录]```
    *	-r 复制目录
    *	-p保留文件属性(修改时间也可以保留)

* 命令名称：```move[原文件或目录][目标目录]```

* 命令名称：cat（查看文件）tac（反向显示）

    ​					more（分页显示）-q退出

    ​					less（可向上分页）pageup翻页up翻行

    ​									/ +关键词，可搜索

    ​					head -n（查看前几行）

    ​					tail -n （查看后几行）-f（动态变化）

* 命令名称： ==ln -s（软链接）不加（硬链接）==

    * ​	硬链接即使删除源文件仍然存在

    * 相当如cp -p +同步更新

* 命令名称：```chmod[{ugoa}+{+-=}{rwx}][文件目录]]```==或==```[model = 421][文件或目录]```==或==-R递归修改（改变目录下的所有权限）

    * 改变文件或目录权限

## 2 常用习惯

1. cd+后车 直接到home里

2. startx 转成图像模式

3. init  3 转成文本界面

4. reboot重启ip

5. ==vi写入模式==，按a进入编辑模式

6. 写入模式按==ESC==退出写入模式，按==shift：==修改，==wq，q==保存并退出，退出；加==感叹号==强制保存。

7. 暂停==ctrl C==

8. 输入su 进入管理员权限，退出管理员su用户名

9. 解压tar zxvg

10. ==ctrl’+r==撤销操作

11. whereis  所有的位置   which 现在所用的位置

12. make是在python下载的地方

13. 目录树

    ![img](https://img-blog.csdnimg.cn/20190422181541718.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3lpbWlzaXlhbmc=,size_16,color_FFFFFF,t_70)

    

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190422183933682.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3lpbWlzaXlhbmc=,size_16,color_FFFFFF,t_70)

## 3 下载软件的流程

1. 如果需要升级，那么首先可以备份一下 mv
2. 在local 建个文件夹，从将软件下载到文件夹中并解压。
3. 查看一下目录文件==ll==
4. 进入到已解压的文件里进行安装
5. ./configure - -prefix =/usr/local/python3Dir 设置安装目录，且看不到这个文件夹的内容
6. make
7. make install 安装
8. 退出quit（）
9. yum依赖的是python2，如果需要用的话，则要进入==vim  /usr/bin/yum==，还有一个==/usr/libexec/urlgrabber-ext-down==。
10. 创建软连接
    1. cd  /usr/bin
    2. ln -s /usr/local/xxx/bin/xxx   /usr/bin/xxx

### 3.1 安装python

  在终端中输入下面的命令

```
wget http://www.python.org/ftp/python/3.6.4/Python-3.6.4.tgz  
tar -xvzf Python-3.6.4.tgz  
cd Python-3.6.4  
./configure --prefix=/usr/local/xxx 

* 如果没有config.log
	* 因为没有gcc，所以要装
	* sudo apt install build-essential

* 如果没有zlib
	* sudo apt-get install zlib1g-dev libssl-dev
	
make  
sudo make install
```

这些命令会使你的ubuntu下载python3.6.4，并替换你现在的python3版本。

### 3.2 安装python运行环境

  输入sudo passwd 输入root相关密码，输入su，进入超级管理员（如果你没设置过，需要设置root用户密码），也许你在安装时还需要升级你的apt-get，命令行下输入apt-get update

```
sudo apt-get install python
sudo apt-get install python-dev(编译外部模块文件使用的)
sudo apt-get install python-pip
sudo apt-get install libxml*
sudo apt-get install net-tools
sudo apt-get install lsof
```

  python3的话安装pip，命令为sudo apt-get install python3-pip
执行之后，输入python3来确定你是否安装成功，如下图所示显示python3.6.4即安装成功：
![安装成功](https://img-blog.csdn.net/2018051820271845?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpbnlhbjIzMw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

### 3.3 更新pip版本

```
sudo pip install --upgrade pip
```



## 4 常见的问题

* 忘记root密码

  * 使用sudo su root
  * sudo 和 su 的区别就是 su 仅仅取得权限，环境还是用户的环境，而sudo是全部的权限

* 当没有网络的时候

  * ipconfig -a查看用户名
  * cat /etc/resolv.conf  查看dns
  * 进入vi /etc/sysconfig/network-scripts/ifcfg-ens32
  * 修改bootproto = static,onboot = yes
  * 增加GATEWAY = ==网关地址==，IPADOR = ==网关地址最后一位改一下==，NETMASK = ==子网掩码255.255.255.0==,DSN1 = ==DSN1==,DSN2 = ==DSN2==.
  * 其中本机的网关地址为==192.168.78.2==​   

* gedit GUI文本编辑器（Ubuntu）

# linux ubuntu学习

## 一 常用习惯

* 关闭图像模式
  * sudo systemctl set-default multi-user.target
    　　sudo reboot

* 开启图像
  * sudo systemctl set-default graphical.target
    　　sudo reboot

## 二 常见问题

* apt-get 下载的位置/var/cache/apt/archives
* `sudo service network-manager restart`==重新联网==
* apt install ```*pinyin*``
* sudo passwd 更改UNIX密码

## 三 关于联网

* 桥接模式（VMnet0）

  * 利用真实网卡和真实计算机进行互通，好处是配置简单
  * 不仅仅和自己的真实机通信，如果有同网段的其他计算机也可以直接访问
  * 坏处是占用网段的IP

* NAT模式（VMnet8）

  * 是虚拟机的假网卡和真实机的网卡进行通信
  * 只能和自己的真实机通信，好处是不用占真实网段的IP地址
  * 可联网

* Host-only（VMnet1）

  * 和NAT一样，除了最后一点可联网
  * 他只能和自己的主机通信  

  ## 四 配置SecureCRT

* ip addr 查看网卡信息

* ssh localhost  查看ssh状态

* sudo passwd root

* 安装openssh-server

* vim /etc/ssh/sshd_config

* 添加一行 PermitRootLogin yes

* 重启service ssh restart

## 五好用的linux插件

* thefuck

```
sudo apt update
sudo apt install python3-dev python3-pip python3-setuptools
sudo pip3 install thefuck
```

