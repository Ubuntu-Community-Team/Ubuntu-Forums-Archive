---
title: "mySQL installation in Edgy"
date: 2007-01-08
forum: General Help
---

### Post by midspot on 2007-01-08
I've been working on this for a few days now and cannot get it to work in edgy. In dapper I had no troubles.

I install mysql-server via synaptic and then run the commands as follows:

sudo gedit /etc/mysql/my.cnf
and comment out the bind-address=127.0.0.1

then
/usr/bin/mysql_install_db 
mysqladmin -u root password mypassword
mysqladmin -h root@local-machine-name -u root -p password mypassword

and I get this error on the last command

/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

no matter how I enter the machine name (by name, IP, or localhost)

I have tried this on two different edgy machines with the same results.

What gives?

---

