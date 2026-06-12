---
title: "MySQL configuration questions"
date: 2012-10-21
forum: General Help
---

### Post by kgriff on 2012-10-21
I ahve installed mysql 5.5.24 using Synaptic.  I'm not new to sql databases, but I am new to mysql.  I'm using the MySQL reference manual as I attempt to understand and configure everything.  So far, I'm not making much headway.  I'm stuck right now trying to start the database and connect as a specific user. (In this case, I want to connect as user 'mysql')
As suggested in the ref man I've made a backup of the data directory, and then run
>mysql_install_db -user=mysql
in order to recreate the data directory, with default tables, with 'mysql' as the owner.
This part worked.
Now, if I start mysql, again as shown in the ref man using
>service mysql start
the database does in fact start.  This has been confirmed by
>mysqladmin version
However, when I start the database in this manner, it appears that I am connected as no user, or user ' '
I believe this because if I execute
>mysqlshow
I see only two databases, 'information_schema' and 'test', even though the table 'mysql' exists in the data directory.

The ref man also references starting the database using
mysqld_safe --user=mysql &
When I do this, it doesn't appear as though the database starts.  (Yes, I did stop the database prior to running this command.)
I say this doesn't start the database because 'mysqlshow' returns the following error:
mysqlshow: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Now, as I said, I'm brand new to mysql and am somewhat confused and completely stuck at this point.  Can anyone help me get past this point?

---

### Post by steeldriver on 2012-10-22
I'm pretty new to mysql myself (with about 1yr of basic MSSQL experience) but here's my take fwiw

First off, I'm a bit confused by your terminology - you don't really start a database, you start the server and then *use *a particular database 

The server itself should start automatically after installing / configuring (and at subsequent boot time) - then you start the *client *(mysql) to connect to it - either specifying an initial catalog (database)

```
$ mysql -u *user *[-p] *database*
```or with default initial catalog and then switching to the desired DB from within mysql via the 'USE' command

```
$ mysql -u *user *[-p]
> use mysql;

```

There should be no need to start or stop the server

---

### Post by kgriff on 2012-10-25
I'll try to fix my terminology and better explain what I'm asking.
First, I did use the term "database" when I should have used "server".
I stopped the server for two reasons, both having to do with the fact that I'm a rank beginner following the MySQL Reference Manual:
1.  In order to create a backup of the data directory /var/lib/mysql
    a. I did this because I'm a chicken and find that I've bailed myself out many times by having a backup.  Additionally, I wanted to run mysql_install_db as user mysql in order to recreate the directory owned by mysql
2.  Following the instructions in the reference manual, it suggested stopping and restarting the server to ensure these functions would work.  This seemed prudent, so I stopped the server.

This is where I began to get lost.  The reference manual shows two different ways to restart the server, but only one of them works.  As stated in my earlier message 
>service mysql start
starts the server, but
>mysqld_safe --user=mysql &
does not.
In addition, again according to the ref man
>mysqlshow
should show the three databases that are, by default after running mysql_install_db, located in the data directory.  These should be
information_schema
mysql
test
However, of these three I can only see 'information_schema' and 'test'.

So, essentially, I'm uncertain as to why one start command works and the other doesn't.  I also don't know why I can only see two of the three tables that exist.

---

