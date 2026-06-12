---
title: "911226 - mysql_pconnect error"
date: 2013-03-16
forum: General Help
---

### Post by hamidi on 2013-03-16
hi
i get the following error in precise:
[Sun Mar 10 12:14:21 2013] [error] [client 10.25.25.90] PHP Fatal error:  Call to undefined function mysql_pconnect() in /var/www/includes/database.php on line 32
at the line mysql_pconnect is used.
what's the problem and how can i resolve it?
thx

---

### Post by solarghost on 2013-03-16
Seems like you are trying to call a function that does not exist.

The actual problem however is that you have _not_ provided enough information for anyone to help you.

Read [this]("http://ubuntuforums.org/showthread.php?t=1422475").

---

