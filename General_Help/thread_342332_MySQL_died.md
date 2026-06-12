---
title: "MySQL died?"
date: 2007-01-19
forum: General Help
---

### Post by Airjoe on 2007-01-19
Maybe a month or so ago, I installed MySQL on my Kubuntu box. I logged in, set up a table or two, blah blah, it worked fine.

Recently, it stopped working. I don't use MySQL often, so I don't know when it happened. But I went to check it out with Webmin, and it said it wasn't started, so I hit the start button in webmin, but it didn't work.

So I tried to login with phpmyadmin, but I got that error that says #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

So I SSH'd into my box, and issued the "/etc/init.d/mysql start" command, but it times out and says:

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


So I went into /var/run/mysqld, but there is no .sock file there. Like I said, I don't know when this happened. I have a very basic system and I only use it as a server. 

For some reason, I think perhaps postfix or maybe courier-imap might've done something.  I think it was working before I installed and setup those, but now it's not. Not sure though. 

Anyway, how can I fix this?

Thanks!

---

### Post by SyvanX on 2007-01-20
Have you checked your mysql logs for any extra information?
```
tail /var/log/mysql.log
tail /var/log/mysql.err
```

If you don't have any super-custom my.cnf file installed, you can probably start by trying to let aptitude reinstall mysql automatically.

If you want to keep your config run this first
```
sudo cp /etc/mysql/my.cnf /etc/mysql/my.cnf.bak
```

Then reinstall mysql
```
sudo aptitude reinstall mysql-server mysql-client
```

To reinstate your previous config file:
```
sudo cp /etc/mysql/my.cnf.bak /etc/mysql/my.cnf
```

Then re-start mysql:
```
sudo /etc/init.d/mysql restart
```

---

