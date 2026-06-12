---
title: "No access in mysql"
date: 2013-12-12
forum: General Help
---

### Post by tmcginnis5901 on 2013-12-12
I recently installed a fresh version of 13.10 and then installed mysql.  Now when I go to do anything in mysql I continuously get "Access Denied".  Are there any other set procedures I need to do so I can have access to at least create a database?

---

### Post by r-senior on 2013-12-12
How did you install mysql?

What are you running that gives you 'Access Denied'?

---

### Post by r-senior on 2013-12-12
It should just be a matter of:

```
sudo apt-get install mysql-server
```

Follow the prompts to enter a root password during installation.

Then connect:

```
mysql -u root -p
```

Enter the password set during installation.

---

### Post by nerdtron on 2013-12-12
You forgot your password entered on the mysql root password?

How to reset the root password for mysql:
1. service mysql stop
2. mysqld_safe --skip-grant-tables &
3. mysql -u root
4. mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit
5. service mysql stop
6. service mysql start
7. mysql -u root -p


Creating a user and assigning database to a user:
1. Login as root.
2. CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'userpassword';
3. GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
4. FLUSH PRIVILEGES;

---

### Post by tmcginnis5901 on 2013-12-22
I am using ubuntu 13.10.
I installed mysql-server using the software center.  Never received any prompts to do anything.
I uninstalled mysql-server using ubuntu software center.
I installed mysql-server using apt-get.  Never received any prompts to do anything.
I followed the directions provided by nerdtron.
When I tried to run 'mysql -u root -p' and entered the password I had created (the one in place of "NEW_ROOT_PASSWORD") it said:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

Something is wrong.

---

### Post by nerdtron on 2013-12-23
Try purging mysql-server package. Then reinstall.

```
 sudo apt-get purge mysql-server
sudo apt-get remove mysql-server
sudo apt-get autoclean

```

---

### Post by zeljkojagust on 2013-12-23
I would recommend Percona version of MySQL server. Here is how you can do it:
[http://www.percona.com/doc/percona-server/5.5/installation/apt_repo.html](http://www.percona.com/doc/percona-server/5.5/installation/apt_repo.html)

When you start the installation, installer will ask you to provide root user pasword. After installation is done create/edit .my.cnf file in your /root folder so it looks like this:

[mysql] 
prompt="\u@\d> " 
user=root 
password="PASS_ENTERED_FOR _ROOT_WHILE_INSTALLING"

 [client] 
user=root 
password="PASS_ENTERED_FOR _ROOT_WHILE_INSTALLING"

After you did it you can start mysql cli by entering the following command:
sudo su -c "mysql" -

---

### Post by tmcginnis5901 on 2013-12-23
I followed nerdtron's purging and re-installed but I still do not get prompted for any information during the install.  Here is the output from the install.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/11.2 kB of archives.
After this operation, 118 kB of additional disk space will be used.
Selecting previously unselected package mysql-server.
(Reading database ... 319145 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.5.34-0ubuntu0.13.10.1_all.deb) ...
Setting up mysql-server (5.5.34-0ubuntu0.13.10.1) ...

---

### Post by devine.steve on 2013-12-23
Here are nerdtron's suggestions again.:
Do these 
1. service mysql stop
2. mysqld_safe --skip-grant-tables &
3. mysql -u root
4. mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit
5. service mysql stop
6. service mysql start
7. mysql -u root -p

What he is doing is having you first stop the server - then restart it without the grant tables - this essentially leaves the front door wide open to the server and then you can go ahead and get that root password set. 
Then stop and restart it. 
If that doesn't work check to see if it's even running:
"ps -ef |grep mysqld"

---

### Post by tmcginnis5901 on 2013-12-23
Well, I run into several problems with those instructions.

The step where you update the user table does not seem to update anything.  This is the response I get.

Query OK, 0 rows affected (0.00 sec)
Rows matched: 4  Changed: 0  Warnings: 0

Step 6 does not stop the server.  It just responds:

stop: Unkown job: mysql

And yes, the server is running.
4     0  6396 24490  20   0  13836  3004 poll_s S    pts/4      0:00 sudo mysqld_safe --skip-grant-tables
4     0  6397  6396  20   0   2272   596 wait   S    pts/4      0:00 /bin/sh /usr/bin/mysqld_safe --skip-grant-tables
4   103  6758  6397  20   0 326172 33324 poll_s Sl   pts/4      0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-grant-tables --log-error=/var/log/mysql/error.log --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
0  1000  6808 24490  20   0   4444   804 pipe_w S+   pts/4      0:00 grep --color=auto mysql

So I tried killing it with kill -15 but it was still running so I had to use kill -9 and kill all its children by hand.

And when I use mysql -u root  -p it gives me access denied.

---

### Post by Iowan on 2013-12-23
I don't expect this to work, but try **mysql -u root **

---

### Post by steeldriver on 2013-12-23
I think the mysql-server package is just an empty package that depends  on the current version - the package you actually need to reconfigure to  perform the password setting step is whatever it depends on  (mysql-server-**5.5** or whatever)

```

$ sudo debconf-show --listowners | grep mysql
mysql-server-5.5

```

```

sudo dpkg-reconfigure **mysql-server-5.5**

```

I don't think purging / resinstalling will help since the password information is in a mysql table (i.e. it is regarded as 'user data' not 'configuration files')

---

### Post by devine.steve on 2013-12-23
Sorry - were you running these as a regular user or as root?
If you were doing it as a unprivileged user - Try it again using sudo 

If you were doing it as root then after the command :
 mysqld_safe --skip-grant-tables& 
check to see if mysqld is running ( ps -ef|grep mysqld )

---

### Post by tmcginnis5901 on 2013-12-28
Well, I finally found an answer from a thread back in 2008.  

There are two entries in the mysql user table that have blank user names.  Once I deleted these two entries, made sure my root passwords where correct, everything worked fine.

And for those who continually say it does, the ubuntu distribuition DOES NOT ask for any input when it is installed.

---

