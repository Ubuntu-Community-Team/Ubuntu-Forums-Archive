---
title: "Mysql error"
date: 2007-04-12
forum: General Help
---

### Post by dearblues on 2007-04-12
can anyone help me?

i get this error while trying to remove @ install my mysql-server

Setting up mysql-server-5.0 (5.0.24a-9ubuntu2) ...
* Stopping MySQL database server mysqld                                                                              [ ok ]
* /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
* Starting MySQL database server mysqld                                                                              [ ok ]
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.


FYI. i have delete the debian-start, my.cnf and all other file in /etc/mysql. what can i do to get back all the file?

p/s: sory if this goes to the wrong thread

---

