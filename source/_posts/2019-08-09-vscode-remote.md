---
title: vs code remote使用入门
date: 2019-08-09 15:40:37
tags: vscode
---

<img src="/blog_img/vscode_struct.png">

先放一张 vs code remote 的原理图来解释 vs code remote 能做到的事情。简而言之，你在本地的 vs code 能做到的事情，vs code remote 都能做到，只不过本地的 vs code 使用的本机的环境，vs code remote 使用的是你连接的远程服务器或本机子系统的环境而已。

下面介绍使用方法<!--more--> 

## 步骤一：下载并安装 vs code 1.35稳定版及后续版本

这一步没什么好说的，去官网下就好了

官网地址：https://code.visualstudio.com/

## 步骤二：安装 Remote Development 扩展

<img src="/blog_img/vscode_step2.png">

打开 vs code，点击左侧扩展图标，搜索安装 Remote Development 扩展包。

## 步骤三：连接远程服务器

<img src="/blog_img/vscode_step3.png">

点击左下角的图标，连接远程服务器

<img src="/blog_img/vscode_step3_1.png">

如果之前已经配置过 host，可直接点击相应的后 host 名称连接，如果没有配置过，点击 “configure SSH Hosts” 选择 “.ssh/config” 文件配置 host，配置方法如下：

```
Host devbox
    HostName 0.0.0.0  // ip
    User silver       // 用户名
    Port 22
    IdentityFile ~/.ssh/id_rsa
```

IdentityFile 处填私钥文件的路径，生成 ssh 密钥的命令如下，ssh 的配置应该在创建服务器的时候就完成了，这里不再赘述：

```
// "xxxxxxxx@xxx.com"处填写自己的邮箱地址
ssh-keygen -t rsa -C "xxxxxxxx@xxx.com"
```

至此，配置便已经完成，接下来的操作和在本地的 vs code 上操作一模一样，打开文件夹作为工作区，安装相应扩展，稍微要注意的是，现在扩展可以安装在两个地方，一个是 local，一个是 remote，大部分时候 vs code 能自动帮我们判断需要安装到哪个位置

在编辑 go 或者 python 文件时，vs code 会推荐安装一些包，在安装墙外的包时，记得配置proxy

<img src="/blog_img/vscode_step3_2.png">