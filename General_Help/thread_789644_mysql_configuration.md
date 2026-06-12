---
title: "mysql configuration"
date: 2008-05-10
forum: General Help
---

### Post by mastermind123 on 2008-05-10
Hi, Im trying to create a lamp server.

after installing mysql, I am trying to access mysql to change my root password.  However this is the error i get when I type this command:

mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run

plz help...thx!!

p.s.  also how can I create other user accounts for the database

thanks!

---

### Post by rturner on 2008-05-10
I don't know what your error is, but I never use a space between -u and root

mysql -uroot -ppassword

---

### Post by mmichalik on 2008-05-10
I would shutdown the mysql server:

sudo /etc/init.d/mysqld stop
sudo /etc/init.d/mysqld start

and then try to log in again.  If it still gives you an error, try the following:

sudo dpkg-reconfigure mysql-server-5.0

that will allow you to reset the root password to what ever you would like it to be.

and then try

mysql -u root -p NEW_PASSWORD

---

