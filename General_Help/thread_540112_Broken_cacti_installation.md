---
title: "Broken cacti installation"
date: 2007-09-01
forum: General Help
---

### Post by Yodude on 2007-09-01
So i installed cacti , first i got a dialog boxsaying something about confiruing libphp-adobd, i went on with it, then i was opted to confirue Cacti's database, the installer told me to enter a password for the myql admin account , I did, and it turned out that that was wrong. It seems the cacti installation only works if the mysql admin account is set with no password, so i tried so delete the password of the mysql admin account by using "mysql -u root" but i got this error "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock", so please can someone help me recover my Cacti installation ?! Cuz it's like TOTALLY broke :(

---

