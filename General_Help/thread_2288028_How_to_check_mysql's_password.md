---
title: "How to check mysql's password?"
date: 2015-07-23
forum: General Help
---

### Post by andy140 on 2015-07-23
I install mysql on my ubuntu 14.04 with &#65306;sudo apt-get install mysql-server-5.6

and it  automatically create a user(mysql) on my ubuntu OS, now I want to check some

files in the datadir, and I need change user  to mysql, but I don't mysql's passwd. Please

help me,thank you in advance.

here are some output on my shell:

bd@ubuntu:/var/lib/mysql$ ls
auto.cnf  debian-5.6.flag  ibdata1  ib_logfile0  ib_logfile1  jssdb  mysql  mysql_upgrade_info  performance_schema
bd@ubuntu:/var/lib/mysql$ cd jssdb/
-bash: cd: jssdb/: Permission denied
bd@ubuntu:/var/lib/mysql$ ls -l jssdb/
ls: cannot open directory jssdb/: Permission denied
bd@ubuntu:/var/lib/mysql$ ls -l
total 110612
-rwxr-xr-x 1 mysql mysql       56 Jul 23 11:03 auto.cnf
-rwxr-xr-x 1 root  root         0 Jul 23 11:02 debian-5.6.flag
-rwxr-xr-x 1 mysql mysql 12582912 Jul 24 08:57 ibdata1
-rwxr-xr-x 1 mysql mysql 50331648 Jul 24 08:57 ib_logfile0
-rwxr-xr-x 1 mysql mysql 50331648 Jul 23 11:02 ib_logfile1
drwx------ 2 mysql mysql     4096 Jul 24 10:00 jssdb
drwxr-xr-x 2 mysql root      4096 Jul 23 11:03 mysql
-rwxr-xr-x 1 root  root         6 Jul 23 11:03 mysql_upgrade_info
drwxr-xr-x 2 mysql mysql     4096 Jul 23 11:03 performance_schema
bd@ubuntu:/var/lib/mysql$ su mysql

---

### Post by QIII on 2015-07-23
Hello!

Look [here]("https://help.ubuntu.com/lts/serverguide/mysql.html") at the last command under the heading "Configuration".

You should create a new password.

To change the MySQL root password, in a terminal enter:

```
sudo dpkg-reconfigure mysql-server-5.**[COLOR="#FF0000"]6[/COLOR]**
```

Notice the change I made in bold red.

---

### Post by andy140 on 2015-07-24
> **QIII said:**
> Hello!

Look [here]("https://help.ubuntu.com/lts/serverguide/mysql.html") at the last command under the heading "Configuration".

You should create a new password.

To change the MySQL root password, in a terminal enter:

```
sudo dpkg-reconfigure mysql-server-5.**[COLOR=#FF0000]6[/COLOR]**
```

Notice the change I made in bold red.
Hi,friend thank you very much,but you may misunderstand my idea.
I don't want to change the root's password in Mysql database.
I wan't to know the user(mysql)'s password in the ubuntu OS,
because once i install the mysql ,The system will create a user
named mysql in ubuntu.

---

### Post by steeldriver on 2015-07-24
You can't log in using the mysql account - it is locked and also doesn't have a valid login shell

If you need to operate on the /var/lib/mysql directory just use sudo

```

$ ls -l /var/lib/mysql/
ls: cannot open directory /var/lib/mysql/: Permission denied
$ 
$ sudo ls -l /var/lib/mysql/
total 28684
-rw-r--r-- 1 mysql mysql        0 Jul 22 13:37 debian-5.5.flag
-rw-rw---- 1 mysql mysql 18874368 Jul 22 13:37 ibdata1
-rw-rw---- 1 mysql mysql  5242880 Jul 22 13:37 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 Feb 16 19:57 ib_logfile1
drwx------ 2 mysql mysql     4096 Jul 22 13:37 mysql
-rw-rw---- 1 mysql mysql        6 Jul 22 13:37 mysql_upgrade_info
drwx------ 2 mysql mysql     4096 Jul 22 13:37 performance_schema

```

---

### Post by Habitual on 2015-07-24
> **andy140 said:**
> once i install the mysql ,The system will create a user named mysql in ubuntu.
[COLOR=#ff0000]You've said this twice, and **it is simply not true**[/COLOR].
/var/lib/mysql is the file system data directory owned by the mysql service.
It is not necessary to change permission on /var/lib/mysql to some other 'user' 

Mysql only installs the root mysql-user account. The rest is up to you to install/configure/maintain and secure.
These users may or may not exist on the local computer system, and mysql certainly does not create them.

Example grant for a remote user from a remote system:
```
 grant all privileges on *.* to <mysql_user@'<some_foreign_IP>' identified by '<password>';flush privileges;"
```

Granting access does not create an account for them "on" the system.
Users of the system are not arbitrarily granted access to mysql.
There is only one mysql-user *(the mysql 'root' account) made during install of mysql-server.
[QUOTE=]su mysql[/QUOTE]  doesn't work because mysql is not a user on the system.
```
sudo grep mysql /etc/passwd
``` = no mysql 'user'.
The mysql-root and localhost root account passwords don't even have to be the same
illustrates these facts.

See also [https://help.ubuntu.com/lts/serverguide/mysql.html](https://help.ubuntu.com/lts/serverguide/mysql.html)

---

