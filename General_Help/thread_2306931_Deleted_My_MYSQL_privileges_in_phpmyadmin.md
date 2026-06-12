---
title: "Deleted My MYSQL privileges in phpmyadmin"
date: 2015-12-20
forum: General Help
---

### Post by astarmathsandphysics on 2015-12-20
By mistake I deleted my root privileges in phpmyadmin.
I can still log in to mysql but do not have any privileges there and about 4 hours of trying have got me nowhere.
How can I recover my root privilleges?

---

### Post by nerdtron on 2015-12-20
You can try to login from the command line. Basically you'll start mysql in "safe mode" where grants are ignored. These steps are for resetting the mysql root password. You can try to re-grant the permissions you have for root  instead.

[FONT=Calibri]1. service mysql stop[/FONT]
 [FONT=Calibri]2. mysqld_safe --skip-grant-tables &[/FONT]
 [FONT=Calibri]3. mysql -u root[/FONT]
 [FONT=Calibri]4. mysql> use mysql;
[/FONT]
   [FONT=Calibri] mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
[/FONT]
 [FONT=Calibri]mysql> flush privileges;[/FONT]
 [FONT=Calibri]mysql> quit
[/FONT]
 [FONT=Calibri]5. service mysql stop[/FONT]
 [FONT=Calibri]6. service mysql start[/FONT]
 [FONT=Calibri]7. mysql -u root -p

You can re-try to grant the priviledges, instead of resetting the password.
[/FONT]
[FONT=Calibri]1. GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
[/FONT]
 [FONT=Calibri]2. FLUSH PRIVILEGES;

Let's see how it goes.
[/FONT]
[FONT=Calibri]
[/FONT]

---

### Post by dragonfly41 on 2015-12-20
[http://stackoverflow.com/questions/1709078/how-can-i-restore-the-mysql-root-user-s-full-privileges](http://stackoverflow.com/questions/1709078/how-can-i-restore-the-mysql-root-user-s-full-privileges)

---

### Post by astarmathsandphysics on 2015-12-20
Saved my life

Not quite actually. The process fails at
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';

because I log in as the root user but dont have root priveleges

Found debian-sys-maint user and password in /etc/mysql/debian.cnf

Can log into mysql and phpmyadmin using these details with full rights

---

