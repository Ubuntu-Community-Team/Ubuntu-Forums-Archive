---
title: "Search for some easy gui tool for mysql"
date: 2019-08-24
forum: General Help
---

### Post by petrogromovo on 2019-08-24
Hello,
I search for some easy gui tool for mysql for my Kubuntu 18 and found this  [https://sourceforge.net/projects/mysqlcc/](https://sourceforge.net/projects/mysqlcc/)
but tring to download it I managed only 
mysqlcc-1.0.2-fc17.1.i686.rpm
file.

1) I did not find has it deb installer ? 
2) Can you advice some easy gui tool for mysql for my Kubuntu 18. I worked with workbench and **DBeaver**. But they both seems not I search...

Thanks!

---

### Post by dragonfly41 on 2019-08-24
I have Oracle MySQL Workbench 6.3 on Ubuntu 16.04 but I confess I don't use it much
since my interest is mainly in NoSQL databases.

There is also DB Browser for SQLite.

---

### Post by Holger_Gehrke on 2019-08-24
What version of Ubuntu are you using ? Up to Ubuntu 18.10 'mysql-workbench' is in the repositories according to packages.ubuntu.com although it's a somewhat older version. Otherwise there are .deb-packages of the current version available at [https://dev.mysql.com/downloads/workbench/](https://dev.mysql.com/downloads/workbench/) for 18.04 and 19.04. There's even a repository there you can add to your sources to keep the program up-to-date.

Holger

---

### Post by QIII on 2019-08-24
It looks like the last update to that was 6 years ago.  It may be well nigh useless.

I use Workbench.  I have it on my machine in my office and I use it to remotely administer the databases on my websites.  I don't have it installed at all on my webservers.  Nor do I have phpMyAdmin or WordPress.  Those last two account for 75 - 95% of attempted attacks.

---

### Post by #&amp;thj^% on 2019-08-24
> **QIII said:**
> 
I use Workbench.  I have it on my machine in my office and I use it to remotely administer the databases on my websites.  I don't have it installed at all on my webservers.  Nor do I have phpMyAdmin or WordPress.  Those last two account for 75 - 95% of attempted attacks.

+1 for mysql-workbench, Also have it installed on just one server.
Also seen about the same % with the two mentioned. (phpMyAdmin or WordPress)

---

