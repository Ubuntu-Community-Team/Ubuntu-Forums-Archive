---
title: "MySQL"
date: 2007-10-27
forum: General Help
---

### Post by geekylove on 2007-10-27
I recently installed the Ubuntu 7.10 Server. I need some help with how to start up MySQL and making databases and tables and such... Does anyone know a good tutorial?
I need the basic steps... for example... how do I connect to MySQL server? telnet? how?

Thanx

---

### Post by TidusBlade on 2007-10-27
You can try [here](http://www.pixel2life.com/tutorials/mysql/). It has helped me with photoshop, Cinema 4D, HTML and Python alot ;)

---

### Post by #Reistlehr- on 2007-10-27
[http://lamphowto.com](http://lamphowto.com)

It's designed for CentOS if i remember right, so change anything like, /etc/rc.d/init.d change to /etc/init.d

Also, skip anything to do with run levels.

If you would like it to start on boot 

edit: /etc/inittab

before exit add

/etc/init.d/mysql start

---

