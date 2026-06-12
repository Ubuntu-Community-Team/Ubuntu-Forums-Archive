---
title: "How to install mysql[my answer]"
date: 2005-07-27
forum: General Help
---

### Post by rn0dal on 2005-07-27
Note I tried this and it worked, if you find a mistake just let me now.

(1) sudo apt-get install mysql-server     |note: you may need to add extra repos|
(2) mysqladmin -u root -p password yourpassword
      ~$Enter password: yourpassword


To connect to server:
~$ mysql -u root -p
Enter password: yourpassword

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 32 to server version: 4.0.23_Debian-3ubuntu2-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+----------+
| Database |
+----------+
| mysql    |
| test     |
+----------+
2 rows in set (0.01 sec)

mysql>quit


Hope that this help.

-r

---

### Post by majikstreet on 2005-07-27
Maybe this should be a HOWTO?

---

### Post by rn0dal on 2005-07-27
OK changed the title, my bad.

-r

---

### Post by rn0dal on 2005-07-27
[QUOTE=majikstreet]Maybe this should be a HOWTO?[/QUOTE]

How do I change the name of the post?


-r

---

### Post by [censored] on 2005-09-23
[QUOTE=rn0dal]Note I tried this and it worked, if you find a mistake just let me now.

(1) sudo apt-get install mysql-server     |note: you may need to add extra repos|
(2) mysqladmin -u root -p password yourpassword
      ~$Enter password: yourpassword

-r[/QUOTE]

I tried this, and the result was: 

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: YES)'


What does it all mean?

---

### Post by phex on 2005-09-23
This means that the mysql server rejected you because perhaps another root user with a different password is already defined. 

delete the directory /var/lib/mysql. this is where all the database data are stored. the user data like the root user is also stored there.

reinstall mysql server and type after it:

mysqladmin -u root root root

this should give you acces to mysql database via console like:

mysql root@localhost -p root

---

### Post by [censored] on 2005-09-23
Cheers did all that. But ...

$ mysqladmin -u root root root
mysqladmin: Unknown command: 'root'

---

### Post by phex on 2005-09-23
oh. i meant:

mysqladmin -u root -p root root

if you have done this, the data is stored in a table in MySql where:
-> User: root
-> Password: root

then you should download mysqlcc and manage the userers and the database with the help of this cool tool. Its better than mysql-admin and mysq-query-browser together if you want to try out mysql for the first time.

---

### Post by [censored] on 2005-09-25
Sorry I've been through this whole procedure from the top atleast twice.

I've uninstalling everything on my deb database with "mysql" in the name, using the --purge option. Then I've even tried rebooting, just incase there was some obscure mysql process still running.

But everytime I try to do this:

> 
$ mysqladmin -u root -p password 7monkeys
Enter password:7monkeys

I get this:
> 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: YES)'

I'm starting to think mysql on linux is just a fairytale.

NOTE:7monkeys isn't really my pw. It's just a pw I chose by way of example.

---

### Post by [censored] on 2005-09-27
Ok, got it working using a variant of the suggestions here:

[http://dev.mysql.com/doc/mysql/en/resetting-permissions.html](http://dev.mysql.com/doc/mysql/en/resetting-permissions.html)

Using this, I've managed to get it to the "show databases;" stage described by the OP on this thread. So presumably, everything else is working ok too. *touch wood*

The page contains two suggestions for how to reset your mysql password in a Unix environment. I found the second one worked, with the slight variation of: 

$sudo mysqld --skip-grant-tables --user=root

instead of:
 
$mysqld --skip-grant-tables --user=root

---

### Post by chiok on 2005-10-04
Howdy.  I had the same problem and I thought it would be helpful to add each step on how I got this to work.  I didn't realise at first that the unofficial ubuntu 5.04 guide sets the root password to 'db_user_password' which was throwing me off.

    * Add extra repositories to sources.list
    * sudo apt-get install mysql-server
    * mysqladmin -u root password db_user_password
    * Comment out skip-networking in /etc/mysql/my.conf
    * sudo mysql_install_db
    * mysql -u root -p 
    * Enter Password: db_user_password
    * mysql> create database whatever;
    * mysql> show databases;

---

### Post by Zensunni on 2005-12-13
Hey, I got this working, and I'll share what I did...

If you have connection errors with an already tried install:

$sudo rm -rf /var/lib/mysql
$sudo apt-get remove mysql-server (don't know if it's necissary, but it's what I did)

If you've done the aforementioned steps or are installing freshly:

$sudo apt-get install mysql-server (installes server =>scrolling text commences and asks if you're sure)
$sudo gedit /etc/mysql/my.cnf

Change:
"bind-address                     = 127.0.0.1"
to:
"# bind-address                     = 127.0.0.1"
Save and exit my.cnf

$mysqladmin -u root password db_user_password*
$sudo mysql_install_database
$mysql -u root -p
(enter password*)
mysql>create database (name_of_server<any name is fine, just pick one>)
      ->\q

I already had MySQLCC installed from before, so I just opened it (go to ubuntuguide.org for how-to install MySQLCC). Then I entered this data in:

Name: (name_of_server<use the name you picked>)
Hostname: localhost
Username: root
Password: db_user_password*

Then It should connect. Now, as for the 

*for command: $mysqladmin -u root password db_user_password.
I don't know if "db_user_password" was a place to enter your own password, or if db_user_password is actually what you have to type as a password that has been setup by apt-get.

Could somebody give some light to this becaues I'm using db_user_password right now and would like to change it if I could.

---

