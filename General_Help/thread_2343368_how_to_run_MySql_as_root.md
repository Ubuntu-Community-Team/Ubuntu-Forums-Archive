---
title: "how to run MySql as root"
date: 2016-11-15
forum: General Help
---

### Post by flex567 on 2016-11-15
I have MySQL installed: 
If I type mysql --version I get :
```

seba@seba-H81-D3:~$ mysql --version
mysql  Ver 14.14 Distrib 5.7.16, for Linux (x86_64) using  EditLine wrapper

```

Now I would like to run it as a root user, how can I do that? During installation I wasn't prompted for any password.

If I try 
mysql -u root -p and press enter without entering the password I get:
```

seba@seba-H81-D3:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

---

### Post by TWj2X6Ln4F on 2016-11-15
Have you tried running the same command without the -p option?

If that doesn't work, try re-installing and setting a password.

---

### Post by flex567 on 2016-11-15
```
seba@seba-H81-D3:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

How should I reinstall? What is the preferred way?

---

### Post by QIII on 2016-11-15
Hello!

You should not need to reinstall if all you are trying to do is set/reset the root password.

Run ```
sudo dpkg-reconfigure mysql-server-*.*
```

where *.* is your version.

---

### Post by yancek on 2016-11-15
The simplest way to begin a setup of mysql is to run:  mysql_secure_installation

You will be prompted to create a root user for mysql during this process.  Not sure how that would work at this point for you so try the suggestion above by QIII

---

### Post by flex567 on 2016-11-16
> 
You should not need to reinstall if all you are trying to do is set/reset the root password.

How do I found out which is my MySQL server version?

---

### Post by deadflowr on 2016-11-16
> **flex567 said:**
> How do I found out which is my MySQL server version?
simple way
```
dpkg -l | grep mysql-server
```

---

### Post by flex567 on 2016-11-16
```

seba@seba-H81-D3:~$ dpkg -l | grep mysql-server
ii  mysql-server                                         5.7.16-1ubuntu16.04                                 amd64        MySQL Server meta package depending on latest version
seba@seba-H81-D3:~$ 


```

---

### Post by flex567 on 2016-11-16
I made different assumption about my server version and this is what I get: 

```

**seba@seba-H81-D3:~$** sudo dpkg-reconfigure mysql-server-5.7.16-1
[sudo] password for seba: 
dpkg-query: package 'mysql-server-5.7.16-1' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.7.16-1 is not installed
**seba@seba-H81-D3:~$** sudo dpkg-reconfigure mysql-server-5.7.16
dpkg-query: package 'mysql-server-5.7.16' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.7.16 is not installed
**seba@seba-H81-D3:~$ **sudo dpkg-reconfigure mysql-server-5.7
dpkg-query: package 'mysql-server-5.7' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.7 is not installed
**seba@seba-H81-D3:~$** sudo dpkg-reconfigure mysql-server
**seba@seba-H81-D3:~$** 

```

any ideas?

---

### Post by QIII on 2016-11-16
So you are using ver 5.7

Give that a whirl and let us know what happens!

---

### Post by flex567 on 2016-11-16
```

**seba@seba-H81-D3:~$** sudo dpkg-reconfigure mysql-server5.7
dpkg-query: package 'mysql-server5.7' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server5.7 is not installed
**seba@seba-H81-D3**:~$ sudo dpkg-reconfigure mysql-server-5.7
dpkg-query: package 'mysql-server-5.7' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.7 is not installed
**seba@seba-H81-D3:~$** sudo dpkg-reconfigure mysql-server 5.7
dpkg-query: package '5.7' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: 5.7 is not installed
**seba@seba-H81-D3:~$** sudo dpkg-reconfigure mysql-server-5.7
dpkg-query: package 'mysql-server-5.7' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.7 is not installed
**seba@seba-H81-D3:~$** 


```

---

### Post by QIII on 2016-11-16
OK.

How did you install MySQL initially?

(I see we posted at the same time earlier.  Sorry to make you repeat yourself!)

---

### Post by flex567 on 2016-11-16
I don't remember exactly I think with apt-get

---

### Post by flex567 on 2016-11-16
I purged/deleted it couple of times also

---

### Post by QIII on 2016-11-16
Make sure it is installed from the repo via apt.  Then try without the version number.

If yhat doesn't work, we can probably get you going with one of the other methods while I figure out what the deal is.

---

### Post by flex567 on 2016-11-16
```

**seba@seba-H81-D3:~$** sudo apt-get update
[sudo] password for seba: 
Hit:1 http://si.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://si.archive.ubuntu.com/ubuntu xenial-updates InRelease [95,7 kB]        
Hit:3 http://si.archive.ubuntu.com/ubuntu xenial-backports InRelease                
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease                   
Get:5 http://deb.opera.com/opera stable InRelease [2592 B]                          
Hit:6 http://repo.mysql.com/apt/ubuntu xenial InRelease                            
Get:7 http://si.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [420 kB]
Get:8 http://deb.opera.com/opera stable/non-free amd64 Packages [1831 B]          
Get:9 http://deb.opera.com/opera stable/non-free i386 Packages [1838 B]        
Get:10 http://si.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [414 kB]
Get:11 http://si.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [359 kB]
Get:12 http://si.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [355 kB]
Fetched 1649 kB in 1s (1142 kB/s)                         
Reading package lists... Done
**seba@seba-H81-D3:~$** sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version (5.7.16-1ubuntu16.04).
The following packages were automatically installed and are no longer required:
  libaec0 libarmadillo6 libarpack2 libblas-common libblas3 libctemplate2v5
  libdap17v5 libdapclient6v5 libepsilon1 libevent-core-2.0-5 libfreexl1
  libgeos-3.5.0 libgeos-c1v5 libgfortran3 libgtkmm-2.4-1v5 libhdf4-0-alt libhdf5-10
  libkmlbase1 libkmldom1 libkmlengine1 liblapack3 libmcrypt4 libminizip1
  libnetcdf11 libodbc1 libogdi3.2 libopenjp2-7 libpcrecpp0v5 libpq5 libproj9
  libspatialite7 libsuperlu4 libsz2 libtinyxml2.6.2v5 liburiparser1 libvsqlitepp3v5
  libxerces-c3.1 libzip4 linux-image-extra-4.2.0-35-generic
  linux-image-extra-4.4.0-21-generic linux-image-extra-4.4.0-22-generic
  linux-image-extra-4.4.0-24-generic linux-image-extra-4.4.0-28-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-43-generic odbcinst
  odbcinst1debian2 proj-bin proj-data python-mysql.connector python-pexpect
  python-ptyprocess python-pyodbc python-pysqlite2 vim-runtime
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
**seba@seba-H81-D3:~$** sudo dpkg-reconfigure mysql-server
**seba@seba-H81-D3:~$ **


```

---

### Post by kpatz on 2016-11-16
Here's another way to do it.

1. Stop mysql:```
sudo systemctl stop mysql
```
2. Recreate the socket directory /var/run/mysql (since stopping the service deletes the socket dir)```
sudo mkdir /var/run/mysqld
sudo chown mysql:mysql /var/run/mysqld
```
3. Run mysql manually with the --skip-grant-tables and --skip-networking options:```
sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
```
4. Log into mysql as root.  You won't need the password since you're running with --skip-grant-tables:```
mysql -u root
```
5.  Flush privileges and change the password for the mysql root user:```
FLUSH PRIVILEGES;
SET PASSWORD FOR root@'localhost' = 'new_password_goes_here';
FLUSH_PRIVILEGES;
```
6.  Exit the mysql client and shut down the mysql daemon you started manually:```
mysqladmin shutdown
```
7.  Restart mysql:```
sudo systemctl start mysql
```
8.  Log in to mysql with the new password as root:```
mysql -u root -p
```

---

### Post by flex567 on 2016-11-16
```

**seba@seba-H81-D3:~$** mysql --version
mysql  Ver 14.14 Distrib 5.7.16, for Linux (x86_64) using  EditLine wrapper
**seba@seba-H81-D3:~$** sudo systemctl stop mysql
[sudo] password for seba: 
**seba@seba-H81-D3:~$** sudo mkdir /var/run/mysqld
**seba@seba-H81-D3:~$** sudo chown mysql:mysql /var/run/mysqld
**seba@seba-H81-D3:~$** sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
[1] 18734
seba@seba-H81-D3:~$ 2016-11-16T17:31:19.885516Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2016-11-16T17:31:19.886762Z 0 [Note] /usr/sbin/mysqld (mysqld 5.7.16) starting as process 18735 ...
2016-11-16T17:31:19.888326Z 0 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!

2016-11-16T17:31:19.888347Z 0 [ERROR] Aborting

2016-11-16T17:31:19.888371Z 0 [Note] Binlog end
2016-11-16T17:31:19.888428Z 0 [Note] /usr/sbin/mysqld: Shutdown complete

```

after that run htop in a separate window and saw that mysq is not running.

---

### Post by kpatz on 2016-11-16
I didn't get that error when I tried it.

Try adding --user=mysql when running it: ```
sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking --user=mysql &
```

---

### Post by flex567 on 2016-11-16
```

**seba@seba-H81-D3:~$** sudo systemctl stop mysql
[sudo] password for seba: 
**seba@seba-H81-D3:~$** sudo mkdir /var/run/mysqld
mkdir: cannot create directory ‘/var/run/mysqld’: File exists
**seba@seba-H81-D3:~$** sudo chown mysql:mysql /var/run/mysqld
**seba@seba-H81-D3:~$** sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking --user=mysql &
[1] 22429
**seba@seba-H81-D3:~$** mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.16 MySQL Community Server (GPL)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

**mysql>** FLUSH PRIVILEGES;
Query OK, 0 rows affected (0,00 sec)

**mysql>** SET PASSWORD FOR root@'localhost' = 'seba';
ERROR 1133 (42000): Can't find any matching row in the user table
**mysql>** use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
**mysql>** update user set authentication_string=password('seba') where user='root';
Query OK, 0 rows affected, 1 warning (0,04 sec)
Rows matched: 0  Changed: 0  Warnings: 1

**mysql>** exit
Bye
**seba@seba-H81-D3:~$** mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
**seba@seba-H81-D3:~$** mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
**seba@seba-H81-D3:~$** 


```

still not working completely.

---

### Post by kpatz on 2016-11-17
Maybe your root user isn't assigned to localhost?  Run the mysqld daemon like above with the --skip-grant-tables --skip-networking --user=mysql options and run this:```
use mysql;
select host, user from user;

```
Paste the results here.

If your root user is missing or isn't on localhost, create one.  While mysqld is running as above:```
flush privileges;
create user root@localhost identified by 'put_password_here';
grant all privileges on *.* to root@localhost with grant option;
flush privileges;

```

---

### Post by flex567 on 2016-11-17
```


**seba@seba-H81-D3:~$** sudo systemctl stop mysql
[sudo] password for seba: 
**seba@seba-H81-D3:~$** sudo mkdir /var/run/mysqld
**seba@seba-H81-D3:~$** sudo chown mysql:mysql /var/run/mysqld
**seba@seba-H81-D3:~$** sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking --user=mysql &
[1] 4300
**seba@seba-H81-D3:**~$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.16 MySQL Community Server (GPL)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

**mysql>** use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
**mysql>** select host, user from user;
+-----------+------------------+
| host      | user             |
+-----------+------------------+
| localhost | debian-sys-maint |
| localhost | mysql.sys        |
+-----------+------------------+
2 rows in set (0,00 sec)

**mysql>** create user root@localhost identified by 'seba';
ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement
**mysql>** flush privileges;
Query OK, 0 rows affected (0,06 sec)
[B]
mysql>[/B] create user root@localhost identified by 'seba';
ERROR 1396 (HY000): Operation CREATE USER failed for 'root'@'localhost'
**mysql>** create user root@localhost identified by 'put_password_here';
ERROR 1396 (HY000): Operation CREATE USER failed for 'root'@'localhost'



```

---

### Post by kpatz on 2016-11-17
How did you install mysql such that there is no root user in the first place?

While googling your latest error, it seems that dropping the user (even though it doesn't exist) before creating it again fixes it.  So, run mysqld with the --skip-grant-tables etc. again, and try these commands:

```
flush privileges;
drop user root@localhost;
create user root@localhost identified by 'seba';
grant all privileges on *.* to root@localhost with grant option;
flush privileges;

```

Even if the "drop user" command returns the error, try the "create user" command afterward anyway.

P.S. Perhaps you should make your root password something stronger than "seba" especially now that you posted it here. :)

Maybe it'll be better to fully uninstall mysql-server (with --purge) and then reinstall, unless you have databases you need to preserve.

---

### Post by flex567 on 2016-11-17
> How did you install mysql such that there is no root user in the first place? I don't know. I purged it couple of time and install it a couple of times.

It seems that it works now. Thanx. 

How will you exploit my pass. You don't know my ip and I think it is also fire-walled ??
And event then there is no much useful databases on my comp.

---

