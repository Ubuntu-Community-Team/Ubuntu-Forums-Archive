---
title: "[SOLVED] Can't get mysql started"
date: 2008-07-05
forum: General Help
---

### Post by lsutiger on 2008-07-05
I am trying to learn mysql. I am following a tutorial that states to setup the root user first:
sudo /usr/bin/mysqladmin -u root password 'my_scret_pass'

but what I am getting is this:

/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

What could be the problem here?

Off to google!

---

### Post by cpetercarter on 2008-07-05
Try this to set the password for root (ie MySQL's root user, not the Ubuntu root user):

```
mysql -u root
```

and then:

```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
```

See [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by lsutiger on 2008-07-05
Thanx for the reply! but...
```
complexity@linux-1501:/$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

There is a user called debian-sys-maint which is installed by default, that I call log on under. I did a SELECT * FROM mysql.user and the password was set for root to what I set it to.....
Google returned a LOT of submissions, but no clear answer.

---

### Post by cpetercarter on 2008-07-05
If you have already set a root password, you should be able to loginto MySQL with

```
mysql -u root -p
```

after which you will be prompted for your password.

---

### Post by lsutiger on 2008-07-05
I wish it were that easy! lol
```
complexity@linux-1501:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

Is what I am getting
and I am positive I am using the right password. I made it simple in order to get it working.

thanx for the reply!

---

### Post by lsutiger on 2008-07-05
HOLY CRAP!!! Got it working!!! But this is a serious bug that needs to be attended to!
Here's the post that fixed it:
> solved THANKS TO
List: mysql
Subject: RE: installing mysql / error
From: Tom Crimmins <mysql2 () pottcounty ! com>
Date: 2004-12-30 19:32:13
Message-ID: 4D6F6B56C91BD8118ED300E01828E4098C1377 () exmail ! pottcounty ! lan
[Download message RAW]


shutdown the mysql server. Then start it from a command line using:

[PATH TO MYSQL BINS]/mysqld --skip-grant-tables

Then open another command prompt and run 'mysql -u root' and run the
following query:

UPDATE mysql.user SET Password='' WHERE User='root' AND Host='localhost';

Then shutdown the server, and restart it normally. You should then be able
to connect with 'mysql -u root'.
IT WORKED
I OPENED MYSQL ADMINISTRATOR AND GOT IN NOT SPECIFYING A PASSWORD THEN SET ONE UP IN THERE.
I HOPE THIS HELPS OTHERS I WASTED TWO DAYS FINDING THE ANSWER

Hopes that helps anyone who is having this problem!

---

