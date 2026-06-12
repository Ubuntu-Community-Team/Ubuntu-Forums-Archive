---
title: "mysql installation problem"
date: 2013-01-23
forum: General Help
---

### Post by USER1992 on 2013-01-23
i try to install mysql and i follow this steps :

1. sudo apt-get install mysql-server
2. gksudo gedit /etc/mysql/my.cnf
3. Change the line bind-address = 127.0.0.1 to your IP address.
 4 . mysql -u root


why when i try to do step 4 i have the following error?


error: Found option without preceding group in config file: /etc/my.cnf at line: 1
Fatal error in defaults handling. Program aborted

---

### Post by slickymaster on 2013-01-23
Check the charset encoding of the **my.cnf** file, make sure that it is in ASCII.

---

