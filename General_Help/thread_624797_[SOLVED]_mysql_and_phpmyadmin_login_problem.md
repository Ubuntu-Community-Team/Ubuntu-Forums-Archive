---
title: "[SOLVED] mysql and phpmyadmin login problem ????????"
date: 2007-11-27
forum: General Help
---

### Post by myharshdesigner on 2007-11-27
i am having an error in mysql.



harsh@harsh-laptop:~$ mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
harsh@harsh-laptop:~$ 



i have installed mysq and phpmyadmin , apache2 through **synaptic package manager**
i am using ubuntu 7.10

---

### Post by bob31984 on 2007-11-27
Are you sure mysql is running? Try
```
sudo /etc/init.d/mysql start
```

---

### Post by myharshdesigner on 2007-11-27
> harsh@harsh-laptop:~$ sudo /etc/init.d/mysql start
sudo: /etc/init.d/mysql: command not found
harsh@harsh-laptop:~$ 


:(

---

### Post by myharshdesigner on 2007-11-27
i have seen 
```

/etc/init.d/

```

but i did't find any mysql file in init.d

why ?

---

### Post by bob31984 on 2007-11-27
Try
```
sudo mysqld_safe &
```
(the & makes it run in the background). Failing that, try just
```
sudo mysqld
```
and if that doesn't work I suggest you reinstall mysql
```

sudo apt-get remove mysql-server
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mysql-server

```

---

### Post by myharshdesigner on 2007-11-27
Thanks

For your Reply.

but i have solved my problem it was my mistake i did't install mysql-server

i jus installed queary browser and admin section that's why i can't able to log in to my sql account.

but Thanks a lot for your Support.

Thanks
Harsh

---

