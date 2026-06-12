---
title: "tar question cvf and xvf"
date: 2007-01-15
forum: General Help
---

### Post by moonhk on 2007-01-15
Dear Reader

I am using tar cvf to backup my home directory then using tar xvf to restore it. But with below problem.

Cannot change ownership to uid 1000, gid 1000: Operation not permitted

What is the problem ?

Before , I am Sun Solaris user.

My tar script
========
moonhk@hex:~/shell$ cat backup_moon.ksh
# 2007/01/08 eric.leung

DFN=moonhk_`date +%Y%m%d`.tar
DIR=/mnt/backup
echo backup to file ${DIR}/${DFN}
tar cvf ${DIR}/${DFN} --exclude=/home/moonhk/manuals  $HOME/* > /dev/null \
2>/dev/null
echo backup .bashrc and .bash_profile
cp $HOME/.bashrc ${DIR}
cp $HOME/.bash_profile ${DIR}
moonhk@hex:~/shell$

tar file created as below
-rwxrwxrwx 1 root root 3471360 2007-01-16 12:44 moonhk_20070116.tar

Restore the files
==========
root@hex:/mnt/backup# tar xvf *16*.tar

output as below
tar: home/moonhk/www/package.txt~: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
home/moonhk/www/mysql.txt
tar: home/moonhk/www/mysql.txt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
home/moonhk/www/ubuntu_install.txt~
tar: home/moonhk/www/ubuntu_install.txt~: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
home/moonhk/www/mysql.txt~
tar: home/moonhk/www/mysql.txt~: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: home/moonhk/www: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: Error exit delayed from previous errors
root@hex:/mnt/backup#


moonhk@hex:/mnt/backup/home/moonhk/www$ ls -lt
total 224
-rwxrwxrwx 1 root root 1519 2007-01-15 01:50 ubuntu_install.txt
-rwxrwxrwx 1 root root 1475 2007-01-15 01:49 ubuntu_install.txt~
-rwxrwxrwx 1 root root  317 2007-01-15 01:46 mysql.txt
-rwxrwxrwx 1 root root  309 2007-01-15 01:46 mysql.txt~
-rwxrwxrwx 1 root root  215 2007-01-15 00:03 package.txt
-rwxrwxrwx 1 root root  175 2007-01-14 23:45 package.txt~
-rwxrwxrwx 1 root root  421 2007-01-10 14:19 internet_site.txt
-rwxrwxrwx 1 root root  440 2007-01-10 10:40 index.html
-rwxrwxrwx 1 root root 1244 2007-01-07 14:28 ubuntu.html
-rwxrwxrwx 1 root root   12 2007-01-07 02:11 hello.py
-rwxrwxrwx 1 root root  143 2007-01-07 01:20 firstprogram.py
-rwxrwxrwx 1 root root  417 2006-12-27 08:29 apache2.html
-rwxrwxrwx 1 root root   94 2006-12-26 19:18 Apache-vitual-hosts.html
-rwxrwxrwx 1 root root  338 2006-12-26 18:49 resource.html
moonhk@hex:/mnt/backup/home/moonhk/www$

#


In passwd file 
=========
moonhk@hex:/etc$ cat passwd|grep moonhk
moonhk:x:1000:1000:moonhk,,,:/home/moonhk:/bin/bash
moonhk@hex:/etc$


moonhk@hex:/mnt/backup/home/moonhk/www$ uname -a
Linux hex 2.6.15-27-server #1 SMP Fri Dec 8 18:43:54 UTC 2006 i686 GNU/Linux
moonhk@hex:/mnt/backup/home/moonhk/www$

---

