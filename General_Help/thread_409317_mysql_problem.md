---
title: "mysql problem"
date: 2007-04-14
forum: General Help
---

### Post by mojportal on 2007-04-14
I have problem with mysql. After uninstall manualy remove some mysql files with rm -rf (/var/lib/mysql, mysql in init.d and rc2.d, mysql dir in /etc ...). Now I try again install mysql but have some errors about /var/lib/mysql and /etc/mysql/my.cnf. Then manualy create thats directory and files, but whet try start run is failed

 * Stopping MySQL database server mysqld                                 [ OK ]
 * Starting MySQL database server mysqld                                 [fail]

How to force uninstall and then install with new /var/lib/mysql and /etc/mysql?

try 'apt-get remove --purge mysql-server' and then 'apt-get install mysql-server' but that dont create /var/lib/mysql and /etc/mysql

---

### Post by acormack on 2007-04-14
have you got a /etc/mysql directory?

does it contain a my.cnf file?

---

### Post by mojportal on 2007-04-14
After I remove manualy /etc/mysql/my.cnf and reinstall mysql-server in /etc dont exist directory mysql so I manualy create directory mysql and my.cnf. In my.cnf i try put this [http://en.wikipedia.org/wiki/Wikipedia:Database_dump_import_problems/sample_my.cnf](http://en.wikipedia.org/wiki/Wikipedia:Database_dump_import_problems/sample_my.cnf) but in /var/lib dont exist mysql. Then create that directory but mysql dont wont start

---

### Post by acormack on 2007-04-14
This is my default /etc/my.cnf file

I had to rename to mycnf.txt to get it to upload.

Alec

---

### Post by mojportal on 2007-04-14
mysql is fixed. phpmyadmin is now problem. 

in term
robi@phoenix:~$ mysql -u root -p
Enter password: <here type password>
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 5.0.38-Ubuntu_0ubuntu1-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

In phpmyadmin type root and same password give me this
#1045 - Access denied for user 'root'@'localhost' (using password: YES)

When reboot system and type in phpmyadmin root and root password I'm in, but when whatever click return me to login page and then this error again

---

### Post by acormack on 2007-04-15
Robi

Glad you got Mysql working.

>>In phpmyadmin type root and same password give me this
>>#1045 - Access denied for user 'root'@'localhost' (using password: YES)

>>When reboot system and type in phpmyadmin root and root password I'm in, but when whatever >>click return me to login page and then this error again

This makes me think that when you click on the "return me to login page" you are accessing a different hostname than you are immediately after the reboot.

If you reboot and get into phpmyadmin then check precisely what your security settings are for the root user when accessing from different hosts.

I think you may have different passwords for root when accessing from different ip addresses.


Alec

---

