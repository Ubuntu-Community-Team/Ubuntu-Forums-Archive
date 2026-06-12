---
title: "&quot;no such file or directory&quot; when executing executables"
date: 2007-11-04
forum: General Help
---

### Post by baosheng on 2007-11-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/160088](https://bugs.launchpad.net/ubuntu/+bug/160088) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I found a strange problem on my new Ubuntu 7.10 version. If I wanna run some programs, I get "no such file or directory" error. This problem happened even when I am just in the directory of this program. 

For example, i am directory ~. And there is an executable called foo. If I run it by

./foo

Then I will get the output, say foo, no such file or directory.

I have authorized enough privilege to run that program.

I got confused on this problem which has never occurred in my previous 2 years time of using Ubuntu.

Can some one help me?

Sincerely,
Forrest

---

### Post by mragetheottoman on 2007-12-26
i exactly have the same problem....dunno what to do...but waiting..can anyone help us?

---

### Post by taurus on 2007-12-26
What is the name of the program/app that you intend to run and are you in the same directory where that program/app is?  What's the output of this command from a terminal?

```
ls -la
```

---

### Post by k_l_k on 2008-03-12
I am having this exact problem. I wrote a simple C utility to connect to a FTP and download some files, but when I try to run it I get the following:

bash: ./updater: No such file or directory

The output of the ls -la command is below:

tgs@tgs-desktop:~/imdb-updater$ ls -la
total 72
drwxr-xr-x  3 tgs tgs  4096 2008-03-12 12:44 .
drwxr-xr-x 30 tgs tgs  4096 2008-03-12 11:47 ..
-rw-rw-rw-  1 tgs tgs  4964 2008-03-12 12:22 ftplib.h
-rw-------  1 tgs tgs   959 2008-03-12 12:21 main.c
-rw-r--r--  1 tgs tgs  1468 2008-03-12 12:44 main.o
-rw-------  1 tgs tgs   302 2008-03-12 12:44 Makefile
-rwxr-xr-x  1 tgs tgs  2956 2008-03-12 12:44 updater

Thanks in advance for your help.

---

### Post by koenn on 2008-03-12
[https://bugs.launchpad.net/ubuntu/+bug/160088/comments/2](https://bugs.launchpad.net/ubuntu/+bug/160088/comments/2)

---

### Post by bodhi.zazen on 2008-03-12
Another potential problem may occur if you are trying to run from a partition with noexec.

Do you have a separate /home partition ? Other partition ?

If /home you need the defaults in /etc/fstab to read nodev,nosuid

Like this :> /dev/hda5 /home ext3 nodev,nosuid 0 2

---

