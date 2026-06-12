---
title: "cant login to mysql"
date: 2007-11-21
forum: General Help
---

### Post by Green_Star on 2007-11-21
I am trying to work with mySQL, but endup with error. I googled for problem but so far no luck. I can not login to mysql using command prompt and the phpmyadmin, i get following error.

>  mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I even tried with password but no luck

>  mysqladmin -u root -p 
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'


it will be very grateful if some one help me to resolve this. 

by the way mysql was install along with mythtv, mythtv using same mysql without problems. 

Thanks in advance.

---

### Post by eggdeng on 2007-11-22
> I even tried with password
What password did you try with? Did you assign a password to the mysql root user when you installed mysql?

---

### Post by Green_Star on 2007-11-22
I tried with the password which was automatically given when I installed mythtv. It is not looking like a password problem, something related to configuration.

---

### Post by Green_Star on 2007-11-23
bump, .. any one?

---

### Post by StubbTx on 2007-11-23
You might try editing the /etc/mysql/my.conf and looking for the "bind-address" setting.

#bind-address           = 127.0.0.1
bind-address            = 0.0.0.0

I had to change mine to 0.0.0.0 to allow local connections to the mysql server.  

If that doesn't help you might try this thread as well.

[http://forums.mysql.com/read.php?11,34014,46593](http://forums.mysql.com/read.php?11,34014,46593)

---

### Post by superm1 on 2007-11-26
> **Green_Star said:**
> I am trying to work with mySQL, but endup with error. I googled for problem but so far no luck. I can not login to mysql using command prompt and the phpmyadmin, i get following error.


I even tried with password but no luck




it will be very grateful if some one help me to resolve this. 

by the way mysql was install along with mythtv, mythtv using same mysql without problems. 

Thanks in advance.
By default there is no root password.  You either created one during mythtv installation, or there is still no password (in which case you shouldn't use the -p switch)

---

### Post by geirha on 2007-11-26
To log in to mysql as root, when the root user has no password, you must be root (OS user). So, try ```
sudo mysql -u root
``` or simply ```
sudo mysql
```

---

