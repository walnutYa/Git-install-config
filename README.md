# Git安装配置教程

> 简介：一个简单的Git安装配置教程，这里上传的Git版本是 Git-2.27.0-64-bit (windows 64位)。

## 快速开始

首先双击安装 Git-2.27.0-64-bit.exe 程序，在安装过程中可以将安装文件重置位置，也可直接安装到C盘(默认)。随后，点击下一步、下一步...即可完成安装。
Git官网: https://git-scm.com/

```shell
// 1.检测Git是否安装成功(window + R，也可鼠标右键能看到Git Bash Here)
$ git --version

// 2.注册一个邮箱 (如: zhangsan@xxx.com)

// 3.去GitHub官网 or GitLab官网上 用你注册的邮箱注册一个账号

// 4.打开命令行 or 桌面直接鼠标右键选择 Git Bash Here

// 5.配置用户名
$ git config --global user.name "zhangsan" // ("zhangsan"是你自己想要设置的账户名)

// 6.配置邮箱
$ git config --global user.email "zhangsan@xxx.com" // ("zhangsan@xxx.com"是你刚用来注册 GitHub or GitLab 的账号邮箱)

// 7.查看配置
$ git config --global --list

// 8.生成ssh
$ ssh-keygen -t rsa
    // 随后敲三次回车，即可生成公钥、密钥
    // 查看: C:\Users\你的电脑名称\.ssh
        // 密钥: id_rsa
        // 公钥: id_rsa.pub (Git配置用这个)

// 9.登录你的 GitHub or GitLab ，选择 settings / SSH and GPG keys 进入配置
    // 1.点击 New SSH key 新建配置
    // 2.填写你的title
    // 3.填写你的key(用记事本或其他编码软件打开公钥: id_rsa.pub，复制、粘贴即可)
    // 4.点击 Add SSH key 保存配置

// 10.测试配置是否成功
$ ssh -T zhangsan@xxx.com 
    // 能显示 Hi zhangsan! You ve succeessfully ...什么的，就是成功了
    // 如果显示连接超时，也可以在 GitHub or GitLab 上新建一个 repositories ，执行git下载，上传命令测试。

```

## Git常用命令
```shell
// 1.初始化Git
$ git init

// 2.新增一个文件
$ git add README.md

// 3.写要提交文件的注释
$ git commit -m "first commit"

// 4.提交到你要上传的git路径地址上面
$ git remote add origin https://github.com/xxx/xxx.git

// 5.提交文件 并 合并到 master 分支上
$ git push -u origin master

// 1.下载远程git文件
$ git clone https://github.com/xxx/xxx.git

// 1.查看所有分支
$ git branch -a

// 1.查看本地分支
$ git branch

// 1.更新分支
$ git fetch

// 1.查看提交版本
$ git log

// 1.回退到上个版本
$ git reset --hard HEAD^

// 1.回退到提交三个版本之前，3是变数，可依此类推，回退版本
$ git reset --hard HEAD~3

// 1.回退到指定的 commit-id 码
$ git reset --hard commit-id

// 1.强制提交
$ git push -f

// 使用 webstorm 进行版本回退
    // 1.点击项目 右键 -> Show-Histroy -> 选择要回退的版本，右键 Copy Revision Number
    // 2.方法一
        // 1.在 TerMinal 上输入命令 git reset -head XXXXX
        // 2.进行强制提交
        $ git push -f
    // 2.方法二
        // 1.右击项目依次选中: git -> Repository -> Reset HEAD
        // 2.选中Reset Type: Mixed, To Commit: 08d537b4fdc74f880f572e948df9a1e87e2ea41f
        //   (08d537b4fdc74f880f572e948df9a1e87e2ea41f: 这个是我们当前版本的版本号，假如使用这种方式，需要没有 reset hard 之前，先 copy 当前版本)
        // 3.点击Reset按钮
    // 3.方法一 与 方法二 的区别
        // 方法一 是会把回滚版本之后的数据全部抹杀
        // 方法二 会重置一个版本，不会把回滚之后的版本删除掉
        // 团队合作的回滚版本最好是使用第二种方法

```
