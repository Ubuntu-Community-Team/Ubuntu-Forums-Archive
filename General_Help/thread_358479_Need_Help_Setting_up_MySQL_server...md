---
title: "Need Help Setting up MySQL server.."
date: 2007-02-10
forum: General Help
---

### Post by billdotson on 2007-02-10
I think there is some problem when MySQL is installed, and it is not creating a root account.  I want to install MySQL so I can use MythTV.

presbp@PresLinux:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mythtv-common libmyth-0.20 mysql-admin-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/39.5kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Selecting previously deselected package mysql-server.
(Reading database ... 162512 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.24a-9_all.deb) ...
Setting up mysql-server (5.0.24a-9) ...
presbp@PresLinux:~$ mysql
ERROR 1045 (28000): Access denied for user 'presbp'@'localhost' (using password: NO)
presbp@PresLinux:~$

I don't have anything MythTV installed as of right now

---

### Post by gradedcheese on 2007-02-10
Right.  A default mysql has only a 'root' account, with NO PASSWORD

you can log in like this:

mysql -u root

(exit gets you out) Now, if you don't specify '-u root', it tries your account's user name, which doesn't have a MySQL account so it fails.  I hope that clears it up.

You can set the root password, and you can make youself a MySQL account if you wish.

---

### Post by billdotson on 2007-02-10
presbp@PresLinux:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I got that error.

---

### Post by gradedcheese on 2007-02-10
hmmm... try "mysql -u root -p" and give it a blank password.

---

### Post by Gibbs on 2007-02-10
You should have a config file called mysql.ini. Search it for username and password. If it's not there at the bottom try adding

user=myuser
password=mypass

---

### Post by Gibbs on 2007-02-10
My mistake. Having a quick browse it appears there isn't a mysql.ini file (even though theres still a php.ini) for Linux. Your best bet, as I don't know what the config file is, would be to try something like the following in mysqladmin:
```
mysqladmin -u root password 'my_password'
```

See if that sets the password. If it does use it to login.

---

### Post by billdotson on 2007-02-11
nope did not work I tried 

mysql -u root -p
then at the Password: I typed password  instead of giving me 

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I got ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by billdotson on 2007-02-11
ok I got it working.  I am in the      mysql>       prompt now.  Hmm.. not what to do to get MythTV setup and running off these databases?

---

### Post by billdotson on 2007-02-11
Alright people thanks for the help I got MythTV and MySQL up and running.  See ya.  If I need any help later I will post again

---

