---
title: "mysql-server crashes network and DCOP on restart"
date: 2007-12-10
forum: General Help
---

### Post by arczi on 2007-12-10
Hi,

I recently installed mysql server (Ver 14.12 Distrib 5.0.38 ) on Kubuntu Feisty Fawn, and whenever I restart the server via sudo /etc/init.d/mysql restart or attempt to reconfigure through dpkg --configure -a, the server crashes, taking all my network interfaces along with it. From what I see, it's taking down my loopback interface (127.0.0.1) which causes DCOP to crash, in turn crashing KDE. 

Can someone point me in the direction of the possible problem? My my.cnf file has the network address set to 127.0.0.1 -- does this have anything to do with the problem?

When up, the server works flawlessly -- I have wordpress and lighttpd up and running and connecting to the databases without issue.

Also, there are no error messages in /var/log/mysql. The only information I can glean off the problem is to be found in /var/log/daemon.log

This is a sample from a typical cycle of: startup --> attempted restart of server after apt-get installing additional database software (e.g. php-mysql) --> mysql crash -->system shutdown:

```

Dec 10 02:53:37 sloneczna mysqld[4949]: 071210  2:53:37 [Note] /usr/sbin/mysqld: Normal shutdown
Dec 10 02:53:37 sloneczna mysqld[4949]:
Dec 10 02:53:37 sloneczna mysqld[4949]: 071210  2:53:37  InnoDB: Starting shutdown...
Dec 10 02:53:40 sloneczna mysqld[4949]: 071210  2:53:40  InnoDB: Shutdown completed; log sequence number 0 43655
Dec 10 02:53:40 sloneczna mysqld[4949]: 071210  2:53:40 [Note] /usr/sbin/mysqld: Shutdown complete
Dec 10 02:53:40 sloneczna mysqld[4949]:
Dec 10 02:53:40 sloneczna mysqld_safe[7050]: ended
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: ERROR: 1062  Duplicate entry '%-test-' for key 1
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: 071210  2:53:46 [ERROR] Aborting
Dec 10 02:53:46 sloneczna mysqld_safe[7078]:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: 071210  2:53:46 [Note] /usr/sbin/mysqld: Shutdown complete
Dec 10 02:53:46 sloneczna mysqld_safe[7078]:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: Installation of system tables failed!
Dec 10 02:53:46 sloneczna mysqld_safe[7078]:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: Examine the logs in /var/lib/mysql for more information.
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: You can try to start the mysqld daemon with:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: /usr/sbin/mysqld --skip-grant &
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: and use the command line tool
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: /usr/bin/mysql to connect to the mysql
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: database and look at the grant tables:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: shell> /usr/bin/mysql -u root mysql
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: mysql> show tables
Dec 10 02:53:46 sloneczna mysqld_safe[7078]:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: Try 'mysqld --help' if you have problems with paths. Using --log
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: gives you a log in /var/lib/mysql that may be helpful.
Dec 10 02:53:46 sloneczna mysqld_safe[7078]:
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: The latest information about MySQL is available on the web at
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: http://www.mysql.com
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: Please consult the MySQL manual section: 'Problems running mysql_install_db',
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: and the manual section that describes problems on your OS.
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: Another information source is the MySQL email archive.
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: Please check all of the above before mailing us!
Dec 10 02:53:46 sloneczna mysqld_safe[7078]: And if you do mail us, you MUST use the /usr/bin/mysqlbug script!
Dec 10 02:53:47 sloneczna mysqld_safe[7139]: ERROR: 1046  No database selected
Dec 10 02:53:47 sloneczna mysqld_safe[7139]: 071210  2:53:47 [ERROR] Aborting
Dec 10 02:53:47 sloneczna mysqld_safe[7139]:
Dec 10 02:53:47 sloneczna mysqld_safe[7139]: 071210  2:53:47 [Note] /usr/sbin/mysqld: Shutdown complete
Dec 10 02:53:47 sloneczna mysqld_safe[7139]:
Dec 10 02:53:47 sloneczna mysqld_safe[7236]: started
Dec 10 02:53:48 sloneczna mysqld[7239]: 071210  2:53:48  InnoDB: Started; log sequence number 0 43655
Dec 10 02:53:48 sloneczna mysqld[7239]: 071210  2:53:48 [Note] /usr/sbin/mysqld: ready for connections.
Dec 10 02:53:48 sloneczna mysqld[7239]: Version: '5.0.38-Ubuntu_0ubuntu1.1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Dec 10 02:53:51 sloneczna mysqld[7239]: 071210  2:53:51 [Note] /usr/sbin/mysqld: Normal shutdown
Dec 10 02:53:51 sloneczna mysqld[7239]:
Dec 10 02:53:53 sloneczna mysqld[7239]: 071210  2:53:53  InnoDB: Starting shutdown...
Dec 10 02:53:57 sloneczna mysqld[7239]: 071210  2:53:57  InnoDB: Shutdown completed; log sequence number 0 43655
Dec 10 02:53:57 sloneczna mysqld[7239]: 071210  2:53:57 [Note] /usr/sbin/mysqld: Shutdown complete
Dec 10 02:53:57 sloneczna mysqld[7239]:
Dec 10 02:53:57 sloneczna mysqld_safe[7425]: ended
```

---

