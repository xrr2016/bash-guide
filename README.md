<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/2059754/24601246/753a7f36-1858-11e7-9d6b-7a0e64fb27f7.png" alt="bash logo"/>
</p>

## 目录
  1. [基础操作](#1-basic-operations)  
    1.1. [文件操作](#11-file-operations)  
    1.2. [文本操作](#12-text-operations)  
    1.3. [目录操作](#13-directory-operations)  
    1.4. [SSH, 系统信息, 网络操作](#14-ssh-system-info--network-operations)  
    1.5. [进程监控操作](#15-process-monitoring-operations)
  2. [基础 Shell 编程](#2-basic-shell-programming)  
    2.1. [变量](#21-variables)  
    2.2  [数组](#22-array)  
    2.3. [字符串替换](#23-string-substitution)  
    2.4. [函数](#24-functions)  
    2.5. [条件](#25-conditionals)  
    2.6. [循环](#26-loops)  
  3. [技巧](#3-tricks)  
  4. [调试](#4-debugging)
  

# 1. 基础操作
### a. `export`
显示所有的环境变量. 如果你要获取特定的变量的详细信息, 使用 `echo $VARIABLE_NAME`
```bash
export
```
示例:
```bash
$ export
AWS_HOME=/Users/adnanadnan/.aws
LANG=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LESS=-R

$ echo $AWS_HOME
/Users/adnanadnan/.aws
```

### b. `whatis`
whatis 命令展示用户指令, 系统调用, 库函数以及其他指令在手册页中的描述信息.
```bash
whatis something
```
Example:
```bash
$ whatis bash
bash (1)             - GNU Bourne-Again SHell
```

### c. `whereis`
whereis 命令使用系统自动构建的数据库查找可执行文件, 源文件, 以及手册页面.
```bash
whereis name
```
Example:
```bash
$ whereis php
/usr/bin/php
```

### d. `which`
which 命令在由环境变量 PATH 指定的目录中搜索可执行文件. 这个命令会显示可执行文件的完整路径.
```bash
which program_name 
```
Example:
```bash
$ which php
/c/xampp/php/php
```

### e. clear
清除窗口上的内容.

## 1.1. 文件操作
<table>
   <tr>
      <td><a href="#a-cat">cat</a></td>
      <td><a href="#b-chmod">chmod</a></td>
      <td><a href="#c-chown">chown</a></td>
      <td><a href="#d-cp">cp</a></td>
      <td><a href="#e-diff">diff</a></td>
      <td><a href="#f-file">file</a></td>
      <td><a href="#g-find">find</a></td>
      <td><a href="#h-gunzip">gunzip</a></td>
      <td><a href="#i-gzcat">gzcat</a></td>
      <td><a href="#j-gzip">gzip</a></td>
      <td><a href="#k-head">head</a></td>
   </tr>
   <tr>
      <td><a href="#l-lpq">lpq</a></td>
      <td><a href="#m-lpr">lpr</a></td>
      <td><a href="#n-lprm">lprm</a></td>
      <td><a href="#o-ls">ls</a></td>
      <td><a href="#p-more">more</a></td>
      <td><a href="#q-mv">mv</a></td>
      <td><a href="#r-rm">rm</a></td>
      <td><a href="#s-tail">tail</a></td>
      <td><a href="#t-touch">touch</a></td>
   </tr>
</table>

### a. `cat`
它在 UNIX 或者 Linux 环境下可以用来实现以下目的.  
* 在屏幕上显示文本文件
* 复制文本文件  
* 合并文本文件  
* 创建新的文本文件  
```bash
cat filename
cat file1 file2 
cat file1 file2 > newcombinedfile
cat < file1 > file2 #将文件1复制到文件2
```

### b. `chmod`
chmod 命令表示 "变更模式", 允许你改变文件和文件夹的读取, 写入, 以及执行权限. 查阅这个[链接](https://ss64.com/bash/chmod.html) 获取更多信息.
```bash
chmod -options filename
```

### c. `chown`
chown 命令表示 "变更所有者", 允许你更改给定文件或文件夹的用户和用户组的所有权. 基本用法简单直接, 首先是用户(拥有者), 然后是用户组, 用冒号分隔.
```bash
chown -options user:group filename
```

### d. `cp`
将文件从一个位置复制到另一个位置.  
```bash
cp filename1 filename2
```
`filename1` 是源文件路径, `filename2` 是目标路径.

### e. `diff`
比较文件, 列出他们的不同之处.  
```bash
diff filename1 filename2
```

### f. `file`
判定文件类型.  
```bash
file filename
```
Example:
```bash
$ file index.html
 index.html: HTML document, ASCII text
```
### g. `find`
查找目录中的文件
```bash
find directory options pattern
```
Example:
```bash
$ find . -name README.md
$ find /home/user1 -name '*.png'
```

### h. `gunzip`
解压由 gzip 压缩的文件.  
```bash
gunzip filename
```

### i. `gzcat`
让你能够不解压查看 gzip 压缩的文件.
```bash
gzcat filename
```

### j. `gzip`
压缩文件.
```bash
gzip filename
```

### k. `head`
输出文件的前10行  
```bash
head filename
```

### l. `lpq`
查看打印队列.  
```bash
lpq
```
示例:
```bash
$ lpq
Rank    Owner   Job     File(s)                         Total Size
active  adnanad 59      demo                            399360 bytes
1st     adnanad 60      (stdin)                         0 bytes
```

### m. `lpr`
打印文件  
```bash
lpr filename
```

### n. `lprm`
删除打印队列的某些任务.  
```bash
lprm jobnumber
```

### o. `ls`
列出你的文件. `ls` 命令有很多可选项: `-l` 列出文件的 `long format`, 包含文件的确切大小, 文件所有者, 有权查看它的人, 以及它的最后修改时间. `-a` 列出所有文件, 包括隐藏文件. 查阅这个[链接](https://ss64.com/bash/ls.html)获取更多关于这个命令的信息.
```bash
ls option
```
示例:
<pre>
$ ls -la
rwxr-xr-x   33 adnan  staff    1122 Mar 27 18:44 .
drwxrwxrwx  60 adnan  staff    2040 Mar 21 15:06 ..
-rw-r--r--@  1 adnan  staff   14340 Mar 23 15:05 .DS_Store
-rw-r--r--   1 adnan  staff     157 Mar 25 18:08 .bumpversion.cfg
-rw-r--r--   1 adnan  staff    6515 Mar 25 18:08 .config.ini
-rw-r--r--   1 adnan  staff    5805 Mar 27 18:44 .config.override.ini
drwxr-xr-x  17 adnan  staff     578 Mar 27 23:36 .git
-rwxr-xr-x   1 adnan  staff    2702 Mar 25 18:08 .gitignore
</pre>

### p. `more`
展示文件的第一部分(使用空格键移动, q键退出)  
```bash
more filename
```

### q. `mv`
将文件从一个位置移动到另一个位置.  
```bash
mv filename1 filename2
```
`filename1` 是源文件路径, `filename2` 是目标路径.

它也能被用来重命名文件.
```bash
mv old_name new_name
```

### r. `rm`
删除文件. 对一个文件夹使用这个命令会得到一个错误.
`rm: directory: is a directory`
为删除目录需要传入 `-r` 参数, 它可以递归的删除目录中的内容. 你可以可选的使用 `-f` 标志强制删除文件, 即不需要任何确认.
```bash
rm filename
```

### s. `tail`
输出文件的后10行. 使用 `-f` 标志输出附加的数据.
```bash
tail filename
```

### t. `touch`
更新文件的访问和修改时间戳. 如果文件不存在, 它会被创建.
```bash
touch filename
```
示例:
```bash
$ touch trick.md
```

## 1.2. 文本操作

<table>
    <tr>
      <td><a href="#a-awk">awk</a></td>
      <td><a href="#b-cut">cut</a></td>
      <td><a href="#c-echo">echo</a></td>
      <td><a href="#d-egrep">egrep</a></td>
      <td><a href="#e-fgrep">fgrep</a></td>
      <td><a href="#f-fmt">fmt</a></td>
      <td><a href="#g-grep">grep</a></td>
      <td><a href="#h-nl">nl</a></td>
      <td><a href="#i-sed">sed</a></td>
      <td><a href="#j-sort">sort</a></td>
   </tr>
   <tr>
      <td><a href="#k-tr">tr</a></td>
      <td><a href="#l-uniq">uniq</a></td>
      <td><a href="#m-wc">wc</a></td>
   </tr>
</table>

### a. `awk`
awk is the most useful command for handling text files. It operates on an entire file line by line. By default it uses whitespace to separate the fields. The most common syntax for awk command is
awk 是处理文本文件最有用的命令. 它逐行操作整个文件. 默认使用空格分隔区域. awk 命令最常用的语法是
```bash
awk '/search_pattern/ { action_to_take_if_pattern_matches; }' file_to_parse
```

Lets take following file `/etc/passwd`. Here's the sample data that this file contains:
用 `/etc/passwd` 做例子. 这是这个文件包含的内容:
```
root:x:0:0:root:/root:/usr/bin/zsh
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
```
So now lets get only username from this file. Where `-F` specifies that on which base we are going to separate the fields. In our case it's `:`. `{ print $1 }` means print out the first matching field.
现在让我们只从这个文件获取用户名. `-F` 指定了我们分隔区域的字符. 这里是 `:`. `{ print $1}` 表示打印第一个匹配的区域.
```bash
awk -F':' '{ print $1 }' /etc/passwd
```
After running the above command you will get following output.
运行上面的命令之后你会得到如下的输出.
```
root
daemon
bin
sys
sync
```
For more detail on how to use `awk`, check following [link](https://www.cyberciti.biz/faq/bash-scripting-using-awk).
查阅这个[链接](https://www.cyberciti.biz/faq/bash-scripting-using-awk)获取更多资料.

### b. `cut`
Remove sections from each line of files
删除文件每行中的部分

*example.txt*
```bash
red riding hood went to the park to play
```

*show me columns 2 , 7 , and 9 with a space as a separator*
*显示文件的第2, 7和9行, 用空格分开*
```bash
cut -d " " -f2,7,9 example.txt
```
```bash
riding park play
```

### c. `echo`
Display a line of text
显示一行文本

*display "Hello World"*
```bash
echo Hello World
```
```bash
Hello World
```

*display "Hello World" with newlines between words*
*显示单词中有换行符号的"Hello World"*
```bash
echo -ne "Hello\nWorld\n"
```
```bash
Hello
World
```

### d. `egrep`
Print lines matching a pattern - Extended Expression (alias for: 'grep -E')
打印符合一种模式的文本行 - 扩展表达式 (别名: 'grep -E')

*example.txt*
```bash
Lorem ipsum
dolor sit amet, 
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*display lines that have either "Lorem" or "dolor" in them.*
*显示具有 "Lorem" 或者 "dolor" 的行.*
```bash
egrep '(Lorem|dolor)' example.txt
or
grep -E '(Lorem|dolor)' example.txt
```
```bash
Lorem ipsum
dolor sit amet,
et dolore magna
duo dolores et ea
sanctus est Lorem
ipsum dolor sit
```

### e. `fgrep`
Print lines matching a pattern - FIXED pattern matching  (alias for: 'grep -F')
打印匹配一种模式的文本行 - 固定匹配模式 (别名: 'grep -F')

*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
foo (Lorem|dolor) 
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*Find the exact string '(Lorem|dolor)' in example.txt*
*在 example.txt 中找到包含 '(Loeem|dolor)' 的行*
```bash
fgrep '(Lorem|dolor)' example.txt
or
grep -F '(Lorem|dolor)' example.txt
```
```bash
foo (Lorem|dolor) 
```

### f. `fmt`
Simple optimal text formatter
简单格式化文本

*example: example.txt (1 line)*
```bash
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
```

*output the lines of example.txt to 20 character width*
*输出每行为20个字符宽的 example.txt*
```bash
cat example.txt | fmt -w 20
```
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

### g. `grep`
Looks for text inside files. You can use grep to search for lines of text that match one or many regular expressions, and outputs only the matching lines.
查看文件内的文本. 可以用 grep 命令查找匹配一个或多个正则表达式的文本行, 只输出匹配的行.  
```bash
grep pattern filename
```
示例:
```bash
$ grep admin /etc/passwd
_kadmin_admin:*:218:-2:Kerberos Admin Service:/var/empty:/usr/bin/false
_kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
_krb_kadmin:*:231:-2:Open Directory Kerberos Admin Service:/var/empty:/usr/bin/false
```
You can also force grep to ignore word case by using `-i` option. `-r` can be used to search all files under the specified directory, for example:
也可以使用 `-i` 选项强制让 grep 命令忽略大小写. `-r` 标志可以用来匹配指定目录下的全部文件, 例如:
```bash
$ grep -r admin /etc/
```
And `-w` to search for words only. For more detail on `grep`, check following [link](https://www.cyberciti.biz/faq/grep-in-bash).
`-w` 标记只查找单词. 查阅这个 [链接](https://www.cyberciti.biz/faq/grep-in-bash) 获取更多信息.

### h. `nl`
Number lines of files
文件的行数

*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*show example.txt with line numbers*
*显示带有行数的 example.txt*
```bash
nl -s". " example.txt 
```
```bash
     1. Lorem ipsum
     2. dolor sit amet,
     3. consetetur
     4. sadipscing elitr,
     5. sed diam nonumy
     6. eirmod tempor
     7. invidunt ut labore
     8. et dolore magna
     9. aliquyam erat, sed
    10. diam voluptua. At
    11. vero eos et
    12. accusam et justo
    13. duo dolores et ea
    14. rebum. Stet clita
    15. kasd gubergren,
    16. no sea takimata
    17. sanctus est Lorem
    18. ipsum dolor sit
    19. amet.
```

### i. `sed`
Stream editor for filtering and transforming text
过滤以及转换文本

*example.txt*
```bash
Hello This is a Test 1 2 3 4
``` 

*replace all spaces with hyphens*
*用连字符替换全部空格*
```bash
sed 's/ /-/g' example.txt
```
```bash
Hello-This-is-a-Test-1-2-3-4
```

*replace all digits with "d"*
*用 "d" 替换全部数字*
```bash
sed 's/[0-9]/d/g' example.txt
```
```bash
Hello This is a Test d d d d
```

### j. `sort`
Sort lines of text files
对文件的行排序

*example.txt*
```bash
f
b
c
g
a
e
d
```

*sort example.txt*
*排序 example.txt*
```bash
sort example.txt
```
```bash
a
b
c
d
e
f
g
```

*randomize a sorted example.txt*
*对已排序的 example.txt 随机打乱行*
```bash
sort example.txt | sort -R
```
```bash
b
f
a
c
d
g
e
```

### k. `tr`
Translate or delete characters
翻译或删除字符

*example.txt*
```bash
Hello World Foo Bar Baz!
```

*take all lower case letters and make them upper case*
*让所有小写字符变成大写*
```bash
cat example.txt | tr 'a-z' 'A-Z' 
```
```bash
HELLO WORLD FOO BAR BAZ!
```

*take all spaces and make them into newlines*
*删除所有空格让他们变成换行符*
```bash
cat example.txt | tr ' ' '\n'
```
```bash
Hello
World
Foo
Bar
Baz!
```

### l. `uniq`
Report or omit repeated lines
报告或清除重复的行

*example.txt*
```bash
a
a
b
a
b
c
d
c
```

*show only unique lines of example.txt (first you need to sort it, otherwise it won't see the overlap)*
*显示 example.txt 中独一的行 (首先你要对它进行排序, 否则它不会检查到重复的行)* 
```bash
sort example.txt | uniq
```
```bash
a
b
c
d
```

*show the unique items for each line, and tell me how many instances it found*
*显示每行中独一的项目, 以及告诉我找到了多少实例*
```bash
sort example.txt | uniq -c
```
```bash
    3 a
    2 b
    2 c
    1 d
```

### m. `wc`
Tells you how many lines, words and characters there are in a file.  
告诉你文件的行数, 单词数以及字符数.
```bash
wc filename
```
示例:
```bash
$ wc demo.txt
7459   15915  398400 demo.txt
```
Where `7459` is lines, `15915` is words and `398400` is characters.
`7459` 行, `15915` 个单词, `398400` 个字符.

## 1.3. 目录操作

<table>
   <tr>
      <td><a href="#a-cd">cd</a></td>
      <td><a href="#b-mkdir">mkdir</a></td>
      <td><a href="#c-pwd">pwd</a></td>
   </tr>
</table>

### a. `cd`
Moves you from one directory to other. Running this  
让你从一个目录移动到另一个目录. 运行这个命令
```bash
$ cd
```
moves you to home directory. This command accepts an optional `dirname`, which moves you to that directory.
移动到主目录. 这个命令接受一个可选的 `dirname`, 可以让你移动到那个目录.
```bash
cd dirname
```

### b. `mkdir`
Makes a new directory.  
创建一个新目录.
```bash
mkdir dirname
```

### c. `pwd`
Tells you which directory you currently are in.  
告诉你目前你所在的目录.
```bash
pwd
```

## 1.4. SSH, 系统信息和网络操作

<table>
   <tr>
      <td><a href="#a-bg">bg</a></td>
      <td><a href="#b-cal">cal</a></td>
      <td><a href="#c-date">date</a></td>
      <td><a href="#d-df">df</a></td>
      <td><a href="#e-dig">dig</a></td>
      <td><a href="#f-du">du</a></td>
      <td><a href="#g-fg">fg</a></td>
      <td><a href="#h-finger">finger</a></td>   
      <td><a href="#i-jobs">jobs</a></td>
      <td><a href="#j-last">last</a></td>
   </tr>
   <tr>
      <td><a href="#k-man">man</a></td>
      <td><a href="#l-passwd">passwd</a></td>
      <td><a href="#m-ping">ping</a></td>
      <td><a href="#n-ps">ps</a></td>
      <td><a href="#o-quota">quota</a></td>
      <td><a href="#p-scp">scp</a></td>
      <td><a href="#q-ssh">ssh</a></td>
      <td><a href="#r-top">top</a></td>
      <td><a href="#s-uname">uname</a></td>
      <td><a href="#t-uptime">uptime</a></td>
   </tr>
   <tr>
      <td><a href="#u-w">w</a></td>
      <td><a href="#v-wget">wget</a></td>
      <td><a href="#w-whoami">whoami</a></td>
      <td><a href="#x-whois">whois</a></td>
   </tr>
</table>

### a. `bg`
Lists stopped or background jobs; resume a stopped job in the background.

### b. `cal`
Shows the month's calendar.
显示月历.

### c. `date`
Shows the current date and time.
显示当前日期和时间.

### d. `df`
Shows disk usage.
显示硬盘使用率.

### e. `dig`
Gets DNS information for domain.  
获取域名的 DNS 信息.
```bash
dig domain
```

### f. `du`
Shows the disk usage of files or directories. For more information on this command check this [link](http://www.linfo.org/du.html)
显示文件或者目录的硬盘使用率. 查阅这个 [链接](http://www.linfo.org/du.html) 获取更多信息.
```bash
du [option] [filename|directory]
```
Options:
- `-h` (human readable) Displays output it in kilobytes (K), megabytes (M) and gigabytes (G).
- `-s` (supress or summarize) Outputs total disk space of a directory and supresses reports for subdirectories. 

示例:
```bash
du -sh pictures
1.4M pictures
```

### g. `fg`
Brings the most recent job in the foreground.

### h. `finger`
Displays information about user.
显示用户信息.
```bash
finger username
```
### i. `jobs`
Lists the jobs running in the background, giving the job number.

### j. `last`
Lists your last logins of specified user.  
```bash
last yourUsername
```

### k. `man`
Shows the manual for specified command.  
显示指定命令的手册.
```bash
man command
```

### l. `passwd`
Allows the current logged user to change his password.
运行当前登录用户改变他的密码.

### m. `ping`
Pings host and outputs results.  
```bash
ping host
```

### n. `ps`
Lists your processes.  
列出你的进程.
```bash
ps -u yourusername
```

### o. `quota`
Shows what your disk quota is.  
```bash
quota -v
```

### p. `scp`
Transfer files between a local host and a remote host or between two remote hosts.
在本机于远程机器或者两个远程机器间传递文件.

*copy from local host to remote host*
```bash
scp source_file user@host:directory/target_file
```
*copy from remote host to local host*
```bash
scp user@host:directory/source_file target_file
scp -r user@host:directory/source_folder target_folder
```
This command also accepts an option `-P` that can be used to connect to specific port.  
```bash
scp -P port user@host:directory/source_file target_file
```

### q. `ssh`
ssh (SSH client) is a program for logging into and executing commands on a remote machine.  
ssh 是一个执行登录远程机器的程序.
```bash
ssh user@host
```
This command also accepts an option `-p` that can be used to connect to specific port.  
这个命令也接受一个 `-p` 选项可以指定链接一个特定的端口.
```bash
ssh -p port user@host
```

### r. `top`
Displays your currently active processes.
显示你的当前活动进程.

### s. `uname`
Shows kernel information.  
显示内核信息.
```bash
uname -a
```

### t. `uptime`
Shows current uptime.
显示当前时间.

### u. `w`
Displays who is online.
显示谁在线.

### v. `wget`
Downloads file.  
下载文件.
```bash
wget file
```

### w. `whoami`
Return current logged in username.
返回登录的用户名.
```bash
whoami
```

### x. `whois`
Gets whois information for domain.  
从域名获取 whois 信息.
```bash
whois domain
```

## 1.5. 进程监控操作

<table>
   <tr>
      <td><a href="#a-kill">kill</a></td>
      <td><a href="#b-killall">killall</a></td>
      <td><a href="#c-&">&amp;</a></td>
      <td><a href="#d-nohup">nohup</a></td>
   </tr>
</table>

### a. `kill`
Kills (ends) the processes with the ID you gave.  
杀死 (结束) 你所给的 ID 的进程
```bash
kill PID
```

### b. `killall`
Kill all processes with the name.  
杀死所有带有这个名称的进程
```bash
killall processname
```

### c. &
The `&` symbol instructs the command to run as a background process in a subshell.
`&` 符号指示命令运行在 subshell 后台进程.
```bash
command &
```

### d. `nohup`
nohup stands for "No Hang Up". This allows to run command/process or shell script that can continue running in the background after you log out from a shell.
nohup 命令表示 "不结束". 这让你可以在你退出 shell 命令行之后继续运行你的 命令/进程或者 shell 脚本.
```bash
nohup command
```
Combine it with `&` to create background processes 
结合 `&` 符号创建后台进程
```bash
nohup command &
```

# 2. 基础 Shell 编程


The first line that you will write in bash script files is called `shebang`. This line in any script determines the script's ability to be executed like a standalone executable without typing sh, bash, python, php etc beforehand in the terminal.
你要写的第一行 bash 脚本名为 `shebang`. 这一行决定了脚本的 

```bash
#!/bin/bash
```

## 2.1. 变量

Creating variables in bash is similar to other languages. There are no data types. A variable in bash can contain a number, a character, a string of characters, etc. You have no need to declare a variable, just assigning a value to its reference will create it.
在 bash 创建变量跟其他语言相似. 他们没有数据类型. bash 脚本的变量可以包含数字, 字符, 字符串以及其他. 你对变量的引用进行赋值会创建这个变量而不必声明它.

示例:
```bash
str="hello world"
```

The above line creates a variable `str` and assigns "hello world" to it. The value of variable is retrieved by putting the `$` in the beginning of variable name.
上面的一行创建了一个变量 `str` 然后将 "Hello world" 赋值给它. 变量的值可以用在变量名前添加 `$` 符号检索出来.

示例:
```bash
echo $str   # hello world
```
## 2.2. 数组
Like other languages bash has also arrays. An array is variable containing multiple values. There's no maximum limit on the size of array. Array in bash are zero based. The first element is indexed with element 0. There are several ways for creating arrays in bash. Which are given below.
像其他语言一样 bash 同样拥有数组. 一个数组指的是一个包含多个值得变量. 数组没有最大长度的限制. bash 的数组初始长度为 0. 数组中的第一个元素的索引为 0. 在 bash 中有多种创建数组的方式. 示例如下.

示例:
```bash
array[0] = val
array[1] = val
array[2] = val
array=([2]=val [0]=val [1]=val)
array=(val val val)
```
To display a value at specific index use following syntax:
使用下面的语法显示特定索引的值:

```bash
${array[i]}     # where i is the index
```

If no index is supplied, array element 0 is assumed. To find out how many values there are in the array use the following syntax:
如果没有提供索引值, 返回值假定为数组的第一个元素. 使用下面的语法得到数组的长度.

```bash
${#array[@]}
```

Bash has also support for the ternary conditions. Check some examples below.
Bash 同样支持三元条件判段. 查看下面的示例.

```bash
${varname:-word}    # if varname exists and isn't null, return its value; otherwise return word
${varname:-word}    # 如果变量名存在并且值不为空, 返回他的值; 否则返回 word
${varname:=word}    # if varname exists and isn't null, return its value; otherwise set it word and then return its value
${varname:=word}    # 如果变量名存在且值不为空, 返回它的值; 否则将 word 赋给它, 然后返回他的值.
${varname:+word}    # if varname exists and isn't null, return word; otherwise return null
${varname:+word}    # 如果变量名存在且值不为空, 返回 word; 否则返回空值. 
${varname:offset:length}    # performs substring expansion. It returns the substring of $varname starting at offset and up to length characters
${varname:offset:length}    # 表现为字符串截取. 它返回从 offset 值开始到 length 值结束的字符串片段.
```

## 2.3 字符串替换

Check some of the syntax on how to manipulate strings
查看如何操作字符串的语法

```bash
${variable#pattern}         # if the pattern matches the beginning of the variable's value, delete the shortest part that matches and return the rest
${variable#pattern}         # 如果 pattern 匹配变量的开始处的值, 删除匹配 pattern 的最短的字符串片段, 返回余下的部分.
${variable##pattern}        # if the pattern matches the beginning of the variable's value, delete the longest part that matches and return the rest
${variable%pattern}         # if the pattern matches the end of the variable's value, delete the shortest part that matches and return the rest
${variable%%pattern}        # if the pattern matches the end of the variable's value, delete the longest part that matches and return the rest
${variable/pattern/string}  # the longest match to pattern in variable is replaced by string. Only the first match is replaced
${variable//pattern/string} # the longest match to pattern in variable is replaced by string. All matches are replaced
${#varname}     # returns the length of the value of the variable as a character string
```

## 2.4. 函数
As in almost any programming language, you can use functions to group pieces of code in a more logical way or practice the divine art of recursion. Declaring a function is just a matter of writing function my_func { my_code }. Calling a function is just like calling another program, you just write its name.
跟其他语言一样, 你能够使用函数去更加具有逻辑性或者尝试使用递归去组合片段的代码. 声明函数是只需要写下 function my_func { my_code } 这样的事. 调用函数就像其他的程序那样, 只需要写下他的函数名.  

```bash
function name() {
    shell commands
}
```

示例:
```bash
#!/bin/bash
function hello {
   echo world!
}
hello

function say {
    echo $1
}
say "hello world!"
```

When you run the above example the `hello` function will output "world!". The above two functions `hello` and `say` are identical. The main difference is function `say`. This function, prints the first argument it receives. Arguments, within functions, are treated in the same manner as arguments given to the script.
当你运行上面例子的 `hello` 函数会输出 "world!". 上面的两个函数是不同的. 最主要的不同是函数 `say`. 这个函数打印它得到的第一个参数. 函数的参数, 会像处理脚本参数那样.

## 2.5. 条件语句

The conditional statement in bash is similar to other programming languages. Conditions have many form like the most basic form is `if` expression `then` statement where statement is only executed if expression is true.

```bash
if [expression]; then
    will execute only if expression is true
else
    will execute if expression is false
fi
```

Sometime if conditions becoming confusing so you can write the same condition using the `case statements`.

```bash
case expression in
    pattern1 )
        statements ;;
    pattern2 )
        statements ;;
    ...
esac
```

Expression Examples:

```bash
statement1 && statement2  # both statements are true
statement1 || statement2  # at least one of the statements is true

str1=str2       # str1 matches str2
str1!=str2      # str1 does not match str2
str1<str2       # str1 is less than str2
str1>str2       # str1 is greater than str2
-n str1         # str1 is not null (has length greater than 0)
-z str1         # str1 is null (has length 0)

-a file         # file exists
-d file         # file exists and is a directory
-e file         # file exists; same -a
-f file         # file exists and is a regular file (i.e., not a directory or other special type of file)
-r file         # you have read permission
-s file         # file exists and is not empty
-w file         # you have write permission
-x file         # you have execute permission on file, or directory search permission if it is a directory
-N file         # file was modified since it was last read
-O file         # you own file
-G file         # file's group ID matches yours (or one of yours, if you are in multiple groups)

file1 -nt file2     # file1 is newer than file2
file1 -ot file2     # file1 is older than file2

-lt     # less than
-le     # less than or equal
-eq     # equal
-ge     # greater than or equal
-gt     # greater than
-ne     # not equal
```

## 2.6. 循环语句

There are three types of loops in bash. `for`, `while` and `until`.

Different `for` Syntax:
```bash
for x := 1 to 10 do
begin
  statements
end

for name [in list]
do
  statements that can use $name
done

for (( initialisation ; ending condition ; update ))
do
  statements...
done
```

`while` Syntax:
```bash
while condition; do
  statements
done
```

`until` Syntax:
```bash
until condition; do
  statements
done
```

# 3. 技巧

## Set an alias
Open `bash_profile` by running following command `nano ~/.bash_profile`
> alias dockerlogin='ssh www-data@adnan.local -p2222'  # add your alias in .bash_profile

## To quickly go to a specific directory
nano ~/.bashrc
> export hotellogs="/workspace/hotel-api/storage/logs"

```bash
source ~/.bashrc
cd $hotellogs
```

## Exit traps

Make your bash scripts more robust by reliably performing cleanup.

```bash
function finish {
  # your cleanup here. e.g. kill any forked processes
  jobs -p | xargs kill
}
trap finish EXIT
```

## 保存你的环境变量

When you do `export FOO = BAR`, your variable is only exported in this current shell and all its children, to persist in the future you can simply append in your `~/.bash_profile` file the command to export your variable
```bash
echo export FOO=BAR >> ~/.bash_profile
```

## Accessing your scripts
## 访问你的脚本

You can easily access your scripts by creating a bin folder in your home with `mkdir ~/bin`, now all the scripts you put in this folder you can access in any directory.
你可以通过 `mkdir ~/bin` 命令在主目录创建一个bin目录来访问你的脚本, 现在你可以在任何目录访问你放在这个文件夹里的脚本了.

If you can not access, try append the code below in your `~/.bash_profile` file and after do `source ~/.bash_profile`.
如何你无法访问, 尝试在 `~/.bash_profile` 文件添加下面的代码, 然后运行 `source ~/.bash_profile`
```bash
    # set PATH so it includes user's private bin if it exists
    if [ -d "$HOME/bin" ] ; then
        PATH="$HOME/bin:$PATH"
    fi
```

# 4. 调试
You can easily debug the bash script by passing different options to `bash` command. For example `-n` will not run commands and check for syntax errors only. `-v` echo commands before running them. `-x` echo commands after command-line processing.
你能够通过给 `bash` 命令传入不同的选项轻松的调试 bash 脚本. 例如 `-n` 选项会只检查语法错误而不运行脚本命令. `-v` 会在运行命令之前显示它们. `-x` 会在命令行处理命令的时候显示它.

```bash
bash -n scriptname
bash -v scriptname
bash -x scriptname
```

## Contribution

- Report issues [How to](https://help.github.com/articles/creating-an-issue/)
- Open pull request with improvements [How to](https://help.github.com/articles/about-pull-requests/)
- Spread the word

## Translation
- [Turkish | Türkçe](https://github.com/omergulen/bash-guide)

## License

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
