---
title: "mysql installation fails"
date: 2007-01-15
forum: General Help
---

### Post by pgm8705 on 2007-01-15
when i attempt to install the mysql server using the line:

```
 sudo apt-get install mysql-server
```

I recieve the following error at the end of the process

```
  * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

No clue as to what i need to do to fix this. any help would be great.

---

### Post by zquid on 2007-03-02
I have the exact same problem, found a thread where they said that it was a problem with innodb and adding 
**skip-innodb **
to 
[B]/etc/mysql/my.cnf
[/B]
would fix it. Didn't work for me though
here's my vi** /var/log/syslog** from the installation attempt
```

Mar  2 18:46:55 zquid mysqld_safe[14122]: 070302 18:46:55 [ERROR] Can't start server: cannot resolve hostname!: Success
Mar  2 18:46:55 zquid mysqld_safe[14122]: Installation of system tables failed!
Mar  2 18:46:55 zquid mysqld_safe[14122]: 
Mar  2 18:46:55 zquid mysqld_safe[14122]: Examine the logs in /var/lib/mysql for more information.
Mar  2 18:46:55 zquid mysqld_safe[14122]: You can also try to start the mysqld daemon with:
Mar  2 18:46:55 zquid mysqld_safe[14122]: /usr/sbin/mysqld --skip-grant &
Mar  2 18:46:55 zquid mysqld_safe[14122]: You can use the command line tool
Mar  2 18:46:55 zquid mysqld_safe[14122]: /usr/bin/mysql to connect to the mysql
Mar  2 18:46:55 zquid mysqld_safe[14122]: database and look at the grant tables:
Mar  2 18:46:55 zquid mysqld_safe[14122]: 
Mar  2 18:46:55 zquid mysqld_safe[14122]: shell> /usr/bin/mysql -u root mysql
Mar  2 18:46:55 zquid mysqld_safe[14122]: mysql> show tables
Mar  2 18:46:55 zquid mysqld_safe[14122]: 
Mar  2 18:46:55 zquid mysqld_safe[14122]: Try 'mysqld --help' if you have problems with paths. Using --log
Mar  2 18:46:55 zquid mysqld_safe[14122]: gives you a log in /var/lib/mysql that may be helpful.
Mar  2 18:46:55 zquid mysqld_safe[14122]: 
Mar  2 18:46:55 zquid mysqld_safe[14122]: The latest information about MySQL is available on the web at
Mar  2 18:46:55 zquid mysqld_safe[14122]: http://www.mysql.com
Mar  2 18:46:55 zquid mysqld_safe[14122]: Please consult the MySQL manual section: 'Problems running mysql_install_db',
Mar  2 18:46:55 zquid mysqld_safe[14122]: and the manual section that describes problems on your OS.
Mar  2 18:46:55 zquid mysqld_safe[14122]: Another information source is the MySQL email archive.
Mar  2 18:46:55 zquid mysqld_safe[14122]: Please check all of the above before mailing us!
Mar  2 18:46:55 zquid mysqld_safe[14122]: And if you do mail us, you MUST use the /usr/bin/mysqlbug script!
Mar  2 18:46:55 zquid mysqld_safe[14167]: 070302 18:46:55 [ERROR] Can't start server: cannot resolve hostname!: Success
Mar  2 18:46:55 zquid mysqld_safe[14171]: 070302 18:46:55 [ERROR] Can't start server: cannot resolve hostname!: Success
Mar  2 18:46:56 zquid mysqld_safe[14175]: 070302 18:46:56 [ERROR] Can't start server: cannot resolve hostname!: Success
Mar  2 18:46:56 zquid mysqld_safe[14179]: 070302 18:46:56 [ERROR] Can't start server: cannot resolve hostname!: Success
Mar  2 18:46:58 zquid mysqld_safe[14314]: started
Mar  2 18:46:58 zquid mysqld[14317]: 070302 18:46:58 [ERROR] Can't start server: cannot resolve hostname!: Success
Mar  2 18:46:58 zquid mysqld_safe[14319]: ended
Mar  2 18:47:12 zquid /etc/init.d/mysql[14454]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Mar  2 18:47:13 zquid /etc/init.d/mysql[14454]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Mar  2 18:47:13 zquid /etc/init.d/mysql[14454]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Mar  2 18:47:13 zquid /etc/init.d/mysql[14454]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Mar  2 18:47:13 zquid /etc/init.d/mysql[14454]: 

```

 /usr/sbin/mysqld --skip-grant &
resulted in
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

**/var/run/mysqld/mysqld.sock **

But I don't know what to do about it 
doesn't

---

### Post by zquid on 2007-03-02
Fixed my problem.
I had recently changed from wifi to ethernet so my internal ip was changed.
/etc/mysql/my.cnf
had an entry to bind my old ip-adress. After I changed that entry to localhost everything worked out. Maybe you have a similar problem?

---

### Post by qopit on 2007-08-07
Same problem here with a fixed IP address server running ubuntu server.  Then I found this thread and the following fixed it:[LIST=1]
[*]change the bind-address in /etc/mysql/my.cnf to my static IP (default was 127.0.0.1)
[*]run "dpkg --configure mysql-server-5.0"
[*]run "dpkg --configure mysql-server"
[/LIST]
Thanks!

---

### Post by Wim Sturkenboom on 2007-08-08
@qopit:

Doesn't that imply that the server is now open to the big bad world called internet?

---

### Post by qopit on 2007-08-08
Yes, but this is what I want in this case.  I should have mentioned that.

---

