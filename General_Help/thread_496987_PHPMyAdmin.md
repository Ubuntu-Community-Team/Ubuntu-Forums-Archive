---
title: "PHPMyAdmin"
date: 2007-07-09
forum: General Help
---

### Post by kcirtap on 2007-07-09
I hope this is posted in the right section. I've installed mysql/phpmyadmin/apache and it works fine, except that I cannot login to phpmyadmin because I have no clue what the username/password is. I've tried to change the following lines in the config.inc.php:

//$cfg['Servers'][$i]['controluser']   = 'USER';          // MySQL control user settings
//                                                    // (this user must have read-only
//$cfg['Servers'][$i]['controlpass']   = 'PASSWORD';

Anyone have any ideas?

---

### Post by MikeDX on 2007-07-09
the default username and passwords for mysql are:

username: root
password BLANK

thats "nothing" for password.. zip nada zilch.

---

### Post by kcirtap on 2007-07-10
I've already tried that, it doesn't work..

---

### Post by az on 2007-07-10
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-39085275bc28194cca77d021ec362ff3003b10bc](https://help.ubuntu.com/community/ApacheMySQLPHP#head-39085275bc28194cca77d021ec362ff3003b10bc)

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

