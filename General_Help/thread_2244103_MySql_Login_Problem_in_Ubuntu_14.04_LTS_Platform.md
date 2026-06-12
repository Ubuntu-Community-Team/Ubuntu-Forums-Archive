---
title: "MySql Login Problem in Ubuntu 14.04 LTS Platform"
date: 2014-09-13
forum: General Help
---

### Post by Natural_Divine on 2014-09-13
I have installed mysql: installed successfully

Then I have run mysql_install_db: successful

Then
skm@skmpc:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
skm@skmpc:~$ 


Then
[B]skm@skmpc:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
[/B]
In the last step I am facing problem, and can't login to mysql.

What to do?

---

### Post by cariboo on 2014-09-13
Moved to General Help.

---

### Post by The Cog on 2014-09-14
You normally have to use **mysql -u root -p** to get it to prompt for the password. I don't remember now, but I presume that you were asked for a password during the install?

---

### Post by pissedoffdude on 2014-09-14
The root account is empty by default.  Just hit enter and you should be able to log in.  That said, it's better to set up a root password: ```
sudo mysql_secure_installation 
```

---

