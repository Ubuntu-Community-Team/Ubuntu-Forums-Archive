---
title: "Cannot set MySQL root password - tried multiple methods..."
date: 2020-04-28
forum: General Help
---

### Post by john105 on 2020-04-28
Hi, so I've just installed 20.04 on a new system, and installed MySQL for my web development work. I think it asked me for a password on setup but it didn't work for the root user when I tried to log in. I obviously tried to reset the password using methods which worked on older versions but with no luck. I then found a tutorial specifically for 20.04 and tried that. It failed at the last step. My console output is below:

```

john@Fatman:~$ mysql -Vmysql  Ver 8.0.19-0ubuntu5 for Linux on x86_64 ((Ubuntu))
john@Fatman:~$ sudo systemctl stop mysql
[sudo] password for john: 
john@Fatman:~$ sudo mkdir -p /var/run/mysqld
john@Fatman:~$ sudo chown mysql:mysql /var/run/mysqld
john@Fatman:~$ ps aux | grep mysql
john        7986  0.0  0.0  17536   728 pts/0    S+   19:48   0:00 grep --color=auto mysql
john@Fatman:~$ sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
[1] 7997
john@Fatman:~$ ps aux | grep mysqld
root        7997  0.0  0.0  20540  4572 pts/0    S    19:49   0:00 sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking
mysql       7998  5.2  2.4 2079812 405816 pts/0  Sl   19:49   0:00 /usr/sbin/mysqld --skip-grant-tables --skip-networking
john        8064  0.0  0.0  17536   724 pts/0    S+   19:49   0:00 grep --color=auto mysqld
john@Fatman:~$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7
Server version: 8.0.19-0ubuntu5 (Ubuntu)


Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.


Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.


Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.


mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)


mysql> USE mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A


Database changed
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'mypassword';
**ERROR 1396 (HY000): Operation ALTER USER failed for 'root'@'localhost'**
mysql> quit
Bye

```

Any ideas? Thanks in advance.

J.R.

---

