---
title: "Terminal error (mysql crap)"
date: 2007-06-06
forum: General Help
---

### Post by silentjudas on 2007-06-06
root@xserver:/home# mysqladmin –u root –p create torrentflux

then i get

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
root@xserver:/home# 


I'M IN ROOT. SUDO FREAKIN SU!

---

### Post by rnodal on 2007-06-06
If you installed the ubuntu package for MySQL, you shouldn't have to do that. Instead do:

[code]mysqladmin -u root[\code]
when you first install mysql, a root password is not set, you have to do it after. I don't know which version you have but here is some more info.
[https://help.ubuntu.com/7.04/server/C/mysql.html]("https://help.ubuntu.com/7.04/server/C/mysql.html")

Hope that helps.


-r

---

