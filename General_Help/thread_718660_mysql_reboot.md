---
title: "mysql reboot"
date: 2008-03-08
forum: General Help
---

### Post by maraja on 2008-03-08
hi, 

I am trying to reboot the mysql sever through mysql administrator (installed with synaptics). 
mysql admin asks me the **root** password but none of the passwords I supply are good to proceed. I tried the:
[LIST]
[*]root pw (the one needed to install with apt-get)
[*]mysql root user pw (I can open mysql admin with this one)
[*]debian-sys-maint pw
[/LIST]
none of these allows me to reboot... 

thank you

---

### Post by dabang on 2008-03-08
I'm not quite familiar with mysql, but by "reboot" do you mean "restart" mysqld? If so, this
```
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start
```
should do the trick.

---

### Post by maraja on 2008-03-08
yes, restart is the right term =)

maraja@xps1330:~$ sudo /etc/init.d/mysql stop
Password or swipe finger: 
 * Stopping MySQL database server mysqld                                 [fail] 
=/

---

### Post by danwood76 on 2008-03-08
```

sudo /etc/init.d/mysql restart

```

Does the same thing.
Odd that that command will fail, you could try closing the mysqld in system monitor and running 'sudo /etc/init.d/mysql start' to restart it.

---

### Post by dabang on 2008-03-08
Never seen this message before... :confused: Did you install something like ThinkFinger:
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
Maybe something went wrong there??

---

### Post by maraja on 2008-03-09
```
sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [fail] 
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
```

this time I tried to type the password rather than using my finger, yes *dabang* I am using thinkfinger.

I am not sure if the mysql administration could have been installed something that introduced this issue. Luckily the mysql server is running so I can use the server =)

But I surely need to be able to restart the server everynow and then...

---

### Post by maraja on 2008-03-09
weird, I tried:

```
sudo /usr/bin/mysql-admin
```

and, **apparently**, I am able to stop the server as no warning messages is issued and the startup log states the server is stopped (see image)... **BUT**, in reality, it keeps running...

---

### Post by dabang on 2008-03-10
Hm, that's strange... You should be able to stop mysql as root. Do you find anything useful in /var/log/messages or /var/log/mysql* ?

---

### Post by maraja on 2008-03-11
> **dabang said:**
> Hm, that's strange... You should be able to stop mysql as root. Do you find anything useful in /var/log/messages or /var/log/mysql* ?

no, completely empty...
:(

---

