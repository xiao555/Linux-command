# 每天一个Linux命令

## 文件操作命令

### ls命令

ls命令是linux下最常用的命令。ls命令就是list的缩写,缺省下ls用来打印出当前目录的清单,如果ls指定其他目录,那么就会显示指定目录里的文件及文件夹清单。 通过ls 命令不仅可以查看linux文件夹包含的文件,而且可以查看文件权限(包括目录、文件夹、文件权限)查看目录信息等等。ls 命令在日常的linux操作中用的很多!

#### 1. 命令格式：

ls [选项] [目录名]

#### 2. 命令功能：
列出目标目录中所有的子目录和文件。
#### 3. 常用参数：
-a, –all 列出目录下的所有文件，包括以 . 开头的隐含文件
-A 同-a，但不列出“.”(表示当前目录)和“..”(表示当前目录的父目录)。
-c  配合 -lt：根据 ctime 排序及显示 ctime (文件状态最后更改的时间)配合 -l：显示 ctime 但根据名称排序否则：根据 ctime 排序
-C 每栏由上至下列出项目
–color[=WHEN] 控制是否使用色彩分辨文件。WHEN 可以是'never'、'always'或'auto'其中之一
-d, –directory 将目录象文件一样显示，而不是显示其下的文件。
-D, –dired 产生适合 Emacs 的 dired 模式使用的结果
-f 对输出的文件不进行排序，-aU 选项生效，-lst 选项失效
-g 类似 -l,但不列出所有者
-G, –no-group 不列出任何有关组的信息
-h, –human-readable 以容易理解的格式列出文件大小 (例如 1K 234M 2G)
–si 类似 -h,但文件大小取 1000 的次方而不是 1024
-H, –dereference-command-line 使用命令列中的符号链接指示的真正目的地
–indicator-style=方式 指定在每个项目名称后加上指示符号<方式>：none (默认)，classify (-F)，file-type (-p)
-i, –inode 印出每个文件的 inode 号
-I, –ignore=样式 不印出任何符合 shell 万用字符<样式>的项目
-k 即 –block-size=1K,以 k 字节的形式表示文件的大小。
-l 除了文件名之外，还将文件的权限、所有者、文件大小等信息详细列出来。
-L, –dereference 当显示符号链接的文件信息时，显示符号链接所指示的对象而并非符号链接本身的信息
-m 所有项目以逗号分隔，并填满整行行宽
-o 类似 -l,显示文件的除组信息外的详细信息。   
-r, –reverse 依相反次序排列
-R, –recursive 同时列出所有子目录层
-s, –size 以块大小为单位列出所有文件的大小
-S 根据文件大小排序
–sort=WORD 以下是可选用的 WORD 和它们代表的相应选项：
extension -X status -c
none -U time -t
size -S atime -u
time -t access -u
version -v use -u
-t 以文件修改时间排序
-u 配合 -lt:显示访问时间而且依访问时间排序
配合 -l:显示访问时间但根据名称排序
否则：根据访问时间排序
-U 不进行排序;依文件系统原有的次序列出项目
-v 根据版本进行排序
-w, –width=COLS 自行指定屏幕宽度而不使用目前的数值
-x 逐行列出项目而不是逐栏列出
-X 根据扩展名排序
-1 每行只列出一个文件
–help 显示此帮助信息并离开
–version 显示版本信息并离开
#### 4. 常用范例：
##### 例一：列出/home/peidachang文件夹下的所有文件和目录的详细资料
命令：ls -l -R /home/peidachang
在使用 ls 命令时要注意命令的格式：在命令提示符后，首先是命令的关键字，接下来是命令参数，在命令参数之前要有一短横线“-”，所有的命令参数都有特定的作用，自己可以根据需要选用一个或者多个参数，在命令参数的后面是命令的操作对象。在以上这条命令“ ls -l -R /home/peidachang”中，“ls” 是命令关键字，“-l -R”是参数，“ /home/peidachang”是命令的操作对象。在这条命令中，使用到了两个参数，分别为“l”和“R”，当然，你也可以把他们放在一起使用，如下所示：
命令：ls -lR /home/peidachang
这种形式和上面的命令形式执行的结果是完全一样的。另外，如果命令的操作对象位于当前目录中，可以直接对操作对象进行操作;如果不在当前目录则需要给出操作对象的完整路径，例如上面的例子中，我的当前文件夹是peidachang文件夹，我想对home文件夹下的peidachang文件进行操作，我可以直接输入 ls -lR peidachang，也可以用 ls -lR /home/peidachang。 
##### 例二：列出当前目录中所有以“t”开头的目录的详细内容，可以使用如下命令：
命令：ls -l t*   
可以查看当前目录下文件名以“t”开头的所有文件的信息。其实，在命令格式中，方括号内的内容都是可以省略的，对于命令ls而言，如果省略命令参数和操作对象，直接输入“ ls ”，则将会列出当前工作目录的内容清单。
##### 例三：只列出文件下的子目录
命令：ls -F /opt/soft |grep /$  
列出 /opt/soft 文件下面的子目录
输出：

    [root@localhost opt]# ls -F /opt/soft |grep /$
    jdk1.6.0_16/
    subversion-1.6.1/
    tomcat6.0.32/
    命令：ls -l /opt/soft | grep "^d"
    列出 /opt/soft 文件下面的子目录详细情况
    输出：
    [root@localhost opt]#  ls -l /opt/soft | grep "^d"
    drwxr-xr-x 10 root root      4096 09-17 18:17 jdk1.6.0_16
    drwxr-xr-x 16 1016 1016      4096 10-11 03:25 subversion-1.6.1
    drwxr-xr-x  9 root root      4096 2011-11-01 tomcat6.0.32
##### 例四：列出目前工作目录下所有名称是s 开头的档案，愈新的排愈后面，可以使用如下命令：
命令：ls -ltr s*
输出：

    [root@localhost opt]# ls -ltr s*
    src:
    总计 0
    script:
    总计 0
    soft:
    总计 350644
    drwxr-xr-x  9 root root      4096 2011-11-01 tomcat6.0.32
    -rwxr-xr-x  1 root root  81871260 09-17 18:15 jdk-6u16-linux-x64.bin
    drwxr-xr-x 10 root root      4096 09-17 18:17 jdk1.6.0_16
    -rw-r--r--  1 root root 205831281 09-17 18:33 apache-tomcat-6.0.32.tar.gz
    -rw-r--r--  1 root root   5457684 09-21 00:23 tomcat6.0.32.tar.gz
    -rw-r--r--  1 root root   4726179 10-10 11:08 subversion-deps-1.6.1.tar.gz
    -rw-r--r--  1 root root   7501026 10-10 11:08 subversion-1.6.1.tar.gz
    drwxr-xr-x 16 1016 1016      4096 10-11 03:25 subversion-1.6.1
##### 例五：列出目前工作目录下所有档案及目录;目录于名称后加"/", 可执行档于名称后加"*" 
命令：ls -AF
输出：
[root@localhost opt]# ls -AF
log/  script/  soft/  src/  svndata/  web/
##### 例六：计算当前目录下的文件数和目录数
命令：
ls -l * |grep "^-"|wc -l ---文件个数  
ls -l * |grep "^d"|wc -l    ---目录个数
##### 例七: 在ls中列出文件的绝对路径
命令：ls | sed "s:^:`pwd`/:"
输出：

    [root@localhost opt]# ls | sed "s:^:`pwd`/:" 
    /opt/log
    /opt/script
    /opt/soft
    /opt/src
    /opt/svndata
    /opt/web

##### 例九：列出当前目录下的所有文件（包括隐藏文件）的绝对路径， 对目录不做递归
命令：`find $PWD -maxdepth 1 | xargs ls -ld`
输出：

    [root@localhost opt]# find $PWD -maxdepth 1 | xargs ls -ld
    drwxr-xr-x 8 root root 4096 10-11 03:43 /opt
    drwxr-xr-x 2 root root 4096 2012-03-08 /opt/log
    drwxr-xr-x 2 root root 4096 2012-03-08 /opt/script
    drwxr-xr-x 5 root root 4096 10-11 03:21 /opt/soft
    drwxr-xr-x 2 root root 4096 2012-03-08 /opt/src
    drwxr-xr-x 4 root root 4096 10-11 05:22 /opt/svndata
    drwxr-xr-x 4 root root 4096 10-09 00:45 /opt/web

##### 例十：递归列出当前目录下的所有文件（包括隐藏文件）的绝对路径
命令： find $PWD | xargs ls -ld 
##### 例十一：指定文件时间输出格式
命令：
 ls -tl --time-style=full-iso
输出：
[root@localhost soft]# ls -tl --time-style=full-iso 
总计 350644
drwxr-xr-x 16 1016 1016 4096 2012-10-11 03:25:58.000000000 +0800 subversion-1.6.1
 ls -ctl --time-style=long-iso
输出：
[root@localhost soft]# ls -ctl --time-style=long-iso
总计 350644
drwxr-xr-x 16 1016 1016      4096 2012-10-11 03:25 subversion-1.6.1
#### 扩展：
1. 显示彩色目录列表
    打开/etc/bashrc, 加入如下一行:
    alias ls="ls --color"
    下次启动bash时就可以像在Slackware里那样显示彩色的目录列表了, 其中颜色的含义如下:
    1. 蓝色-->目录
    2. 绿色-->可执行文件
    3. 红色-->压缩文件
    4. 浅蓝色-->链接文件
    5. 灰色-->其他文件


### ssh密钥

#### 生成ssh密钥

密钥是免登录连接服务器的通行证，有种刷脸通行的感觉。如果本地已经存在并且不想另外生成的话，可以跳过此步。

cd ~/.ssh 切换目录后用 ssh-keygen -t rsa -C "用于区分密钥的标识" 生成一对具有相同名字的密钥（默认为 id_rsa 和 id_rsa.pub）：用于本地的私钥和用于服务器的公钥（有 .pub 扩展名）。

如果私钥名字不是默认的话，需要手动加入到被「认证」的私钥列表中，否则每次连接服务器都会提示输入服务器的密码。在遇到了一些坑（文后有说明）后，我觉得设置 SSH config 最为靠谱！

编辑 ~/.ssh/config 文件（如果不存在则 touch ~/.ssh/config 创建一下），添加以下内容：

    Host HOST_ALIAS                       # 用于 SSH 连接的别名，最好与 HostName 保持一致
    HostName SERVER_DOMAIN              # 服务器的域名或 IP 地址
    Port SERVER_PORT                    # 服务器的端口号，默认为 22，可选
    User SERVER_USER                    # 服务器的用户名
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/PRIVATE_KEY     # 本机上存放的私钥路径

#### 服务器端认证

先用 pbcopy < ~/.ssh/PRIVATE_KEY.pub 将公钥复制到剪贴板；通过 ssh USER@SERVER 访问服务器，这时会提示输入密码（它也许只有这么一次「询问」的机会）；成功登录后 vim ~/.ssh/authorized_keys，在合适的位置粘贴并保存退出。

### Linux SSH远程文件/目录传输命令scp

#### 一、scp是什么？

scp是secure copy的简写，用于在Linux下进行远程拷贝文件的命令，和它类似的命令有cp，不过cp只是在本机进行拷贝不能跨服务器，而且scp传输是加密的。可能会稍微影响一下速度。

#### 二、scp有什么用？

1、我们需要获得远程服务器上的某个文件，远程服务器既没有配置ftp服务器，没有开启web服务器，也没有做共享，无法通过常规途径获得文件时，只需要通过scp命令便可轻松的达到目的。

2、我们需要将本机上的文件上传到远程服务器上，远程服务器没有开启ftp服务器或共享，无法通过常规途径上传是，只需要通过scp命令便可以轻松的达到目的。

#### 三、scp使用方法

##### 1、获取远程服务器上的文件

scp -P 2222 root@www.vpser.net:/root/lnmp0.4.tar.gz /home/lnmp0.4.tar.gz

上端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。 root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，:/root/lnmp0.4.tar.gz 表示远程服务器上的文件，最后面的/home/lnmp0.4.tar.gz表示保存在本地上的路径和文件名。还可能会用到p参数保持目录文件的权限访问时间等。

##### 2、获取远程服务器上的目录

scp -P 2222 -r root@www.vpser.net:/root/lnmp0.4/ /home/lnmp0.4/

上端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。-r 参数表示递归复制（即复制该目录下面的文件和目录）；root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，:/root/lnmp0.4/ 表示远程服务器上的目录，最后面的/home/lnmp0.4/表示保存在本地上的路径。

##### 3、将本地文件上传到服务器上

scp -P 2222 /home/lnmp0.4.tar.gz root@www.vpser.net:/root/lnmp0.4.tar.gz

上端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。 /home/lnmp0.4.tar.gz表示本地上准备上传文件的路径和文件名。root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，:/root/lnmp0.4.tar.gz 表示保存在远程服务器上目录和文件名。

##### 4、将本地目录上传到服务器上

scp -P 2222 -r /home/lnmp0.4/ root@www.vpser.net:/root/lnmp0.4/

上 端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。-r 参数表示递归复制（即复制该目录下面的文件和目录）；/home/lnmp0.4/表示准备要上传的目录，root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，:/root/lnmp0.4/ 表示保存在远程服务器上的目录位置。

##### 5、可能有用的几个参数 :

-v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接 , 认证 , 或是配置错误 .

-C 使能压缩选项 .

-4 强行使用 IPV4 地址 .

-6 强行使用 IPV6 地址 .

### wget 命令

Linux系统中的wget是一个下载文件的工具，它用在命令行下。对于Linux用户是必不可少的工具，我们经常要下载一些软件或从远程服务器恢复备份到本地服务器。wget支持HTTP，HTTPS和FTP协议，可以使用HTTP代理。所谓的自动下载是指，wget可以在用户退出系统的之后在后台执行。这意味这你可以登录系统，启动一个wget下载任务，然后退出系统，wget将在后台执行直到任务完成，相对于其它大部分浏览器在下载大量数据时需要用户一直的参与，这省去了极大的麻烦。

wget 可以跟踪HTML页面上的链接依次下载来创建远程服务器的本地版本，完全重建原始站点的目录结构。这又常被称作”递归下载”。在递归下载的时候，wget 遵循Robot Exclusion标准(/robots.txt). wget可以在下载的同时，将链接转换成指向本地文件，以方便离线浏览。
wget 非常稳定，它在带宽很窄的情况下和不稳定网络中有很强的适应性.如果是由于网络的原因下载失败，wget会不断的尝试，直到整个文件下载完毕。如果是服务器打断下载过程，它会再次联到服务器上从停止的地方继续下载。这对从那些限定了链接时间的服务器上下载大文件非常有用。

#### 1．命令格式：

wget [参数] [URL地址]

#### 2．命令功能：

用于从网络上下载资源，没有指定目录，下载资源回默认为当前目录。wget虽然功能强大，但是使用起来还是比较简单：
1）支持断点下传功能；这一点，也是网络蚂蚁和FlashGet当年最大的卖点，现在，Wget也可以使用此功能，那些网络不是太好的用户可以放心了；
2）同时支持FTP和HTTP下载方式；尽管现在大部分软件可以使用HTTP方式下载，但是，有些时候，仍然需要使用FTP方式下载软件；
3）支持代理服务器；对安全强度很高的系统而言，一般不会将自己的系统直接暴露在互联网上，所以，支持代理是下载软件必须有的功能；
4）设置方便简单；可能，习惯图形界面的用户已经不是太习惯命令行了，但是，命令行在设置上其实有更多的优点，最少，鼠标可以少点很多次，也不要担心是否错点鼠标；
5）程序小，完全免费；程序小可以考虑不计，因为现在的硬盘实在太大了；完全免费就不得不考虑了，即使网络上有很多所谓的免费软件，但是，这些软件的广告却不是我们喜欢的。

#### 3．命令参数：

##### 启动参数：

-V, –version 显示wget的版本后退出
-h, –help 打印语法帮助
-b, –background 启动后转入后台执行
-e, –execute=COMMAND 执行`.wgetrc’格式的命令，wgetrc格式参见/etc/wgetrc或~/.wgetrc
记录和输入文件参数：
-o, –output-file=FILE 把记录写到FILE文件中
-a, –append-output=FILE 把记录追加到FILE文件中
-d, –debug 打印调试输出
-q, –quiet 安静模式(没有输出)
-v, –verbose 冗长模式(这是缺省设置)
-nv, –non-verbose 关掉冗长模式，但不是安静模式
-i, –input-file=FILE 下载在FILE文件中出现的URLs
-F, –force-html 把输入文件当作HTML格式文件对待
-B, –base=URL 将URL作为在-F -i参数指定的文件中出现的相对链接的前缀
–sslcertfile=FILE 可选客户端证书
–sslcertkey=KEYFILE 可选客户端证书的KEYFILE
–egd-file=FILE 指定EGD socket的文件名

##### 下载参数：

–bind-address=ADDRESS 指定本地使用地址(主机名或IP，当本地有多个IP或名字时使用)
-t, –tries=NUMBER 设定最大尝试链接次数(0 表示无限制).
-O –output-document=FILE 把文档写到FILE文件中
-nc, –no-clobber 不要覆盖存在的文件或使用.#前缀
-c, –continue 接着下载没下载完的文件
–progress=TYPE 设定进程条标记
-N, –timestamping 不要重新下载文件除非比本地文件新
-S, –server-response 打印服务器的回应
–spider 不下载任何东西
-T, –timeout=SECONDS 设定响应超时的秒数
-w, –wait=SECONDS 两次尝试之间间隔SECONDS秒
–waitretry=SECONDS 在重新链接之间等待1…SECONDS秒
–random-wait 在下载之间等待0…2*WAIT秒
-Y, –proxy=on/off 打开或关闭代理
-Q, –quota=NUMBER 设置下载的容量限制
–limit-rate=RATE 限定下载输率

##### 目录参数：

-nd –no-directories 不创建目录
-x, –force-directories 强制创建目录
-nH, –no-host-directories 不创建主机目录
-P, –directory-prefix=PREFIX 将文件保存到目录 PREFIX/…
–cut-dirs=NUMBER 忽略 NUMBER层远程目录
HTTP 选项参数：
–http-user=USER 设定HTTP用户名为 USER.
–http-passwd=PASS 设定http密码为 PASS
-C, –cache=on/off 允许/不允许服务器端的数据缓存 (一般情况下允许)
-E, –html-extension 将所有text/html文档以.html扩展名保存
–ignore-length 忽略 `Content-Length’头域
–header=STRING 在headers中插入字符串 STRING
–proxy-user=USER 设定代理的用户名为 USER
–proxy-passwd=PASS 设定代理的密码为 PASS
–referer=URL 在HTTP请求中包含 `Referer: URL’头
-s, –save-headers 保存HTTP头到文件
-U, –user-agent=AGENT 设定代理的名称为 AGENT而不是 Wget/VERSION
–no-http-keep-alive 关闭 HTTP活动链接 (永远链接)
–cookies=off 不使用 cookies
–load-cookies=FILE 在开始会话前从文件 FILE中加载cookie
–save-cookies=FILE 在会话结束后将 cookies保存到 FILE文件中
##### FTP 选项参数：

-nr, –dont-remove-listing 不移走 `.listing’文件
-g, –glob=on/off 打开或关闭文件名的 globbing机制
–passive-ftp 使用被动传输模式 (缺省值).
–active-ftp 使用主动传输模式
–retr-symlinks 在递归的时候，将链接指向文件(而不是目录)

##### 递归下载参数：

-r, –recursive 递归下载－－慎用!
-l, –level=NUMBER 最大递归深度 (inf 或 0 代表无穷)
–delete-after 在现在完毕后局部删除文件
-k, –convert-links 转换非相对链接为相对链接
-K, –backup-converted 在转换文件X之前，将之备份为 X.orig
-m, –mirror 等价于 -r -N -l inf -nr
-p, –page-requisites 下载显示HTML文件的所有图片
递归下载中的包含和不包含(accept/reject)：
-A, –accept=LIST 分号分隔的被接受扩展名的列表
-R, –reject=LIST 分号分隔的不被接受的扩展名的列表
-D, –domains=LIST 分号分隔的被接受域的列表
–exclude-domains=LIST 分号分隔的不被接受的域的列表
–follow-ftp 跟踪HTML文档中的FTP链接
–follow-tags=LIST 分号分隔的被跟踪的HTML标签的列表
-G, –ignore-tags=LIST 分号分隔的被忽略的HTML标签的列表
-H, –span-hosts 当递归时转到外部主机
-L, –relative 仅仅跟踪相对链接
-I, –include-directories=LIST 允许目录的列表
-X, –exclude-directories=LIST 不被包含目录的列表
-np, –no-parent 不要追溯到父目录
wget -S –spider url 不下载只显示过程

#### 4．使用实例：

##### 实例1：使用wget下载单个文件
命令：
wget http://www.minjieren.com/wordpress-3.1-zh_CN.zip
说明：
以下的例子是从网络下载一个文件并保存在当前目录，在下载的过程中会显示进度条，包含（下载完成百分比，已经下载的字节，当前下载速度，剩余下载时间）。
##### 实例2：使用wget -O下载并以不同的文件名保存
命令：
: wget -O wordpress.zip http://www.minjieren.com/download.aspx?id=1080
说明：
wget默认会以最后一个符合”/”的后面的字符来命令，对于动态链接的下载通常文件名会不正确。
错误：下面的例子会下载一个文件并以名称download.aspx?id=1080保存
wget http://www.minjieren.com/download?id=1
即使下载的文件是zip格式，它仍然以download.php?id=1080命令。
正确：为了解决这个问题，我们可以使用参数-O来指定一个文件名：
wget -O wordpress.zip http://www.minjieren.com/download.aspx?id=1080
##### 实例3：使用wget –limit -rate限速下载
命令：
wget --limit-rate=300k http://www.minjieren.com/wordpress-3.1-zh_CN.zip
说明：
当你执行wget的时候，它默认会占用全部可能的宽带下载。但是当你准备下载一个大文件，而你还需要下载其它文件时就有必要限速了。
##### 实例4：使用wget -c断点续传
命令：
wget -c http://www.minjieren.com/wordpress-3.1-zh_CN.zip
说明：
使用wget -c重新启动下载中断的文件，对于我们下载大文件时突然由于网络等原因中断非常有帮助，我们可以继续接着下载而不是重新下载一个文件。需要继续中断的下载时可以使用-c参数。
##### 实例5：使用wget -b后台下载
命令：
wget -b http://www.minjieren.com/wordpress-3.1-zh_CN.zip
说明：
对于下载非常大的文件的时候，我们可以使用参数-b进行后台下载。
wget -b http://www.minjieren.com/wordpress-3.1-zh_CN.zip
Continuing in background, pid 1840.
Output will be written to `wget-log'.
你可以使用以下命令来察看下载进度：
tail -f wget-log
##### 实例6：伪装代理名称下载
命令：
wget --user-agent="Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.204 Safari/534.16" http://www.minjieren.com/wordpress-3.1-zh_CN.zip
说明：
有些网站能通过根据判断代理名称不是浏览器而拒绝你的下载请求。不过你可以通过–user-agent参数伪装。
##### 实例7：使用wget –spider测试下载链接
命令：
wget --spider URL
说明：
当你打算进行定时下载，你应该在预定时间测试下载链接是否有效。我们可以增加–spider参数进行检查。
wget --spider URL
如果下载链接正确，将会显示
wget --spider URL
Spider mode enabled. Check if remote file exists.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Remote file exists and could contain further links,
but recursion is disabled -- not retrieving.
这保证了下载能在预定的时间进行，但当你给错了一个链接，将会显示如下错误
wget --spider url
Spider mode enabled. Check if remote file exists.
HTTP request sent, awaiting response... 404 Not Found
Remote file does not exist -- broken link!!!
你可以在以下几种情况下使用spider参数：
定时下载之前进行检查
间隔检测网站是否可用
检查网站页面的死链接
##### 实例8：使用wget –tries增加重试次数
命令：
wget --tries=40 URL
说明：
如果网络有问题或下载一个大文件也有可能失败。wget默认重试20次连接下载文件。如果需要，你可以使用–tries增加重试次数。
##### 实例9：使用wget -i下载多个文件
命令：
wget -i filelist.txt
说明：
首先，保存一份下载链接文件
cat > filelist.txt
url1
url2
url3
url4
接着使用这个文件和参数-i下载
##### 实例10：使用wget –mirror镜像网站
命令：
wget --mirror -p --convert-links -P ./LOCAL URL
说明：
下载整个网站到本地。
–miror:开户镜像下载
-p:下载所有为了html页面显示正常的文件
–convert-links:下载后，转换成本地的链接
-P ./LOCAL：保存所有文件和目录到本地指定目录
##### 实例11：使用wget –reject过滤指定格式下载
命令：
wget --reject=gif ur
说明：
下载一个网站，但你不希望下载图片，可以使用以下命令。
##### 实例12：使用wget -o把下载信息存入日志文件
命令：
wget -o download.log URL
说明：
不希望下载信息直接显示在终端而是在一个日志文件，可以使用
##### 实例13：使用wget -Q限制总下载文件大小
命令：
wget -Q5m -i filelist.txt
说明：
当你想要下载的文件超过5M而退出下载，你可以使用。注意：这个参数对单个文件下载不起作用，只能递归下载时才有效。
##### 实例14：使用wget -r -A下载指定格式文件
命令：
wget -r -A.pdf url
说明：
可以在以下情况使用该功能：
下载一个网站的所有图片
下载一个网站的所有视频
下载一个网站的所有PDF文件
##### 实例15：使用wget FTP下载
命令：
wget ftp-url
wget --ftp-user=USERNAME --ftp-password=PASSWORD url
说明：
可以使用wget来完成ftp链接的下载。
使用wget匿名ftp下载：
wget ftp-url
使用wget用户名和密码认证的ftp下载
wget --ftp-user=USERNAME --ftp-password=PASSWORD url
备注：编译安装
使用如下命令编译安装：

    # tar zxvf wget-1.9.1.tar.gz 
    # cd wget-1.9.1 
    # ./configure 
    # make 
    # make install 
