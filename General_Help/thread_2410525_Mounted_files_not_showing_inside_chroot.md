---
title: "Mounted files not showing inside chroot"
date: 2019-01-16
forum: General Help
---

### Post by amakesh on 2019-01-16
[COLOR=#0C0D0E][FONT=&amp]I have VDS with CentOS and chroot environment with Ubuntu 18.10(had to do this, because app i want to launch needs a libstdc++.so.6 version which is not available for CentOS). 
App i want to launch attempts to connect to MySQL Server through /var/run/mysqld/mysqld.sock but it does not exist inside chroot Ubuntu and also the app need the database from CentOS which has mysql.sock(not mysqld.sock. 
So i did mount --bind /var/lib/mysql /chroot/var/lib/mysql and then 
symlink: ln -s /var/lib/mysql/mysql.sock /var/run/mysqld/mysqld.sock but there is a problem...
when i go to /var/lib/mysql inside chroot and use ls command, there are only „default” files from chroot and mounted files not showing(they showing only in filezilla). So the symlink is useless because there is still no mysql.sock..
How can i fix it??[/FONT][/COLOR]

---

