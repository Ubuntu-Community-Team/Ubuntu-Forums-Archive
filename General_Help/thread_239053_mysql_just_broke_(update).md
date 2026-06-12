---
title: "mysql just broke (update?)"
date: 2006-08-18
forum: General Help
---

### Post by mrashley on 2006-08-18
Were there recent (last 2 weeks) mysql updates? 

Mysql has recently broken and I can't fix it for the life of me. I've installed 5.0 and 4.1 back and forth. I've deleted /var/lib/mysql completely in the hopes that it will recreate. The database itself isn't that important, but I want to get the program itself running. 

:-( :-(  Not sure what to do. Here's what I've done.

```
root@cybil:/var/lib# aptitude install mysql-server
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  mysql-client-5.0 mysql-server-5.0
The following packages will be automatically REMOVED:
  mysql-client-4.1 mysql-server-4.1
The following NEW packages will be installed:
  mysql-client-5.0 mysql-server mysql-server-5.0
The following packages will be REMOVED:
  mysql-client-4.1 mysql-server-4.1
0 packages upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/27.7MB of archives. After unpacking 23.4MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
dpkg: mysql-server-4.1: dependency problems, but removing anyway as you request:
 mythtv-database depends on mysql-server; however:
  Package mysql-server is not installed.
  Package mysql-server-5.0 which provides mysql-server is not installed.
  Package mysql-server-4.1 which provides mysql-server is to be removed.
(Reading database ... 126656 files and directories currently installed.)
Removing mysql-server-4.1 ...
Stopping MySQL database server: mysqld.
dpkg: mysql-client-4.1: dependency problems, but removing anyway as you request:
 mythtv-common depends on mysql-client; however:
  Package mysql-client is not installed.
  Package mysql-client-4.1 which provides mysql-client is to be removed.
Removing mysql-client-4.1 ...
Selecting previously deselected package mysql-client-5.0.
(Reading database ... 126426 files and directories currently installed.)
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.22-0ubuntu6.06_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.22-0ubuntu6.06_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.22-0ubuntu6.06_all.deb) ...
Setting up mysql-client-5.0 (5.0.22-0ubuntu6.06) ...
Setting up mysql-server-5.0 (5.0.22-0ubuntu6.06) ...
Installing new version of config file /etc/init.d/mysql ...
Installing new version of config file /etc/logrotate.d/mysql-server ...
Installing new version of config file /etc/mysql/debian-start ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!


```

I've also done the opposite (5.0 -> 4.1) with a similar outcome.

This is my /var/log/syslog last 30 lines.

```
Aug 18 12:58:18 cybil mysqld_safe[32163]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Aug 18 12:58:18 cybil mysqld_safe[32163]: To do so, start the server, then issue the following commands:
Aug 18 12:58:18 cybil mysqld_safe[32163]: /usr/bin/mysqladmin -u root password 'new-password'
Aug 18 12:58:18 cybil mysqld_safe[32163]: /usr/bin/mysqladmin -u root -h cybil password 'new-password'
Aug 18 12:58:18 cybil mysqld_safe[32163]: See the manual for more instructions.
Aug 18 12:58:18 cybil mysqld_safe[32163]:
Aug 18 12:58:18 cybil mysqld_safe[32163]: NOTE:  If you are upgrading from a MySQL <= 3.22.10 you should run
Aug 18 12:58:18 cybil mysqld_safe[32163]: the /usr/bin/mysql_fix_privilege_tables. Otherwise you will not be
Aug 18 12:58:18 cybil mysqld_safe[32163]: able to use the new GRANT command!
Aug 18 12:58:18 cybil mysqld_safe[32163]:
Aug 18 12:58:18 cybil mysqld_safe[32163]: Please report any problems with the /usr/bin/mysqlbug script!
Aug 18 12:58:18 cybil mysqld_safe[32163]:
Aug 18 12:58:18 cybil mysqld_safe[32163]: The latest information about MySQL is available on the web at
Aug 18 12:58:18 cybil mysqld_safe[32163]: http://www.mysql.com
Aug 18 12:58:18 cybil mysqld_safe[32163]: Support MySQL by buying support/licenses at http://shop.mysql.com
Aug 18 12:58:19 cybil mysqld_safe[32350]: started
Aug 18 12:58:19 cybil mysqld[32353]: InnoDB: The first specified data file ./ibdata1 did not exist:
Aug 18 12:58:19 cybil mysqld[32353]: InnoDB: a new database to be created!
Aug 18 12:58:19 cybil mysqld[32353]: 060818 12:58:19  InnoDB: Setting file ./ibdata1 size to 10 MB
Aug 18 12:58:19 cybil mysqld[32353]: InnoDB: Database physically writes the file full: wait...
Aug 18 12:58:20 cybil mysqld[32353]: 060818 12:58:20  InnoDB: Log file ./ib_logfile0 did not exist: new to be created
Aug 18 12:58:20 cybil mysqld[32353]: InnoDB: Setting log file ./ib_logfile0 size to 5 MB
Aug 18 12:58:20 cybil mysqld[32353]: InnoDB: Database physically writes the file full: wait...
Aug 18 12:58:20 cybil mysqld[32353]: 060818 12:58:20  InnoDB: Log file ./ib_logfile1 did not exist: new to be created
Aug 18 12:58:20 cybil mysqld[32353]: InnoDB: Setting log file ./ib_logfile1 size to 5 MB
Aug 18 12:58:20 cybil mysqld[32353]: InnoDB: Database physically writes the file full: wait...
Aug 18 12:58:21 cybil mysqld[32353]: InnoDB: Doublewrite buffer not found: creating new
Aug 18 12:58:21 cybil mysqld[32353]: InnoDB: Doublewrite buffer created
Aug 18 12:58:21 cybil mysqld[32353]: InnoDB: Creating foreign key constraint system tables
Aug 18 12:58:21 cybil mysqld[32353]: InnoDB: Foreign key constraint system tables created
Aug 18 12:58:21 cybil mysqld[32353]: 060818 12:58:21  InnoDB: Started; log sequence number 0 0
Aug 18 12:58:21 cybil mysqld[32353]: 060818 12:58:21 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Aug 18 12:58:21 cybil mysqld[32353]: 060818 12:58:21 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Aug 18 12:58:21 cybil mysqld[32353]: 060818 12:58:21 [ERROR] Aborting
Aug 18 12:58:21 cybil mysqld[32353]:
Aug 18 12:58:21 cybil mysqld[32353]: 060818 12:58:21  InnoDB: Starting shutdown...
Aug 18 12:58:23 cybil mysqld[32353]: 060818 12:58:23  InnoDB: Shutdown completed; log sequence number 0 43655
Aug 18 12:58:23 cybil mysqld[32353]: 060818 12:58:23 [Note] /usr/sbin/mysqld: Shutdown complete
Aug 18 12:58:23 cybil mysqld[32353]:
Aug 18 12:58:23 cybil mysqld_safe[32391]: ended
Aug 18 12:58:34 cybil /etc/init.d/mysql[32503]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Aug 18 12:58:34 cybil /etc/init.d/mysql[32503]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Aug 18 12:58:34 cybil /etc/init.d/mysql[32503]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Aug 18 12:58:34 cybil /etc/init.d/mysql[32503]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Aug 18 12:58:34 cybil /etc/init.d/mysql[32503]:
Aug 18 12:58:34 cybil /etc/init.d/mysql[32508]: /etc/mysql/debian-log-rotate.conf is obsolete, see /usr/share/doc/mysql-server-5.0/NEWS.Debian.gz

```

It seems the error is that mysql can't BIND to port 3306, but I've searched ubuntuforums and google and I can't believe no one has ever has this problem before. Someone show the me the stupid little thing that happened. I'm really trying to make a good impression of Ubuntu with this new person and I'm doing a really rubbish job!! :-( :-(

---

### Post by .t. on 2006-08-18
Well; I know that this won't help you. But I've just installed and updated an Ubuntu Server, and it all works. Are you sure you don't have a firewall that's blocking it?

---

### Post by dcantin on 2006-08-19
Hi

I also got the "...failed or took more than 6s." while trying to start mysql service. I solve it by correcting a wrong bind address in my /etc/mysql/my.cnf

David

---

### Post by mrashley on 2006-08-20
Ahem. Thank you for the tip. The IP address of the computer had changed recently and so my problem was solved by editing /etc/mysql/my.cnf

```
sudo nano /etc/mysql/my.cnf
```

and finding the lines

```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 192.168.0.100

```

and changed it to

```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = localhost

```

---

