---
title: "how to forbid mysql and apache auto-start"
date: 2006-11-09
forum: General Help
---

### Post by myfavourite on 2006-11-09
i use dapper drake 6.06 ,and use command:
#sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

install php,mysql ,apache to my computer.but i want to forbid them auto-start.

how to do it ? thanks!

---

### Post by dcstar on 2006-11-09
> **myfavourite said:**
> i use dapper drake 6.06 ,and use command:
#sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

install php,mysql ,apache to my computer.but i want to forbid them auto-start.

how to do it ? thanks!

Have a look at your /etc/rc2.d directory and you may well see links that start these, simply delete the links for the things you do not want to start.

---

### Post by eXisor on 2006-11-10
Or the easy way; install sysv-rc-conf from the repository. This'll let you select / unselect the boot startup programs. Simply remove the X's from the apache and mysql entries.

---

### Post by myfavourite on 2006-11-13
i have done it.think you!

---

