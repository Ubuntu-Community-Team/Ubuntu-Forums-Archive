---
title: "su password"
date: 2006-12-29
forum: General Help
---

### Post by spyder0101 on 2006-12-29
I entered only one password for my username durring installation.  Now I need my su password to change my runlevel to 2.  Problem is, it is not the password I entered for my user.  I tried reinstalling to make sure it wasn't a  typo.  Any sugestions?

---

### Post by Ramses de Norre on 2006-12-29
Read [this](http://wiki.ubuntu.com/RootSudo) about ubuntu's sudo system.

You'll need to use sudo to obtain root privilliges (like sudo init 2) and enter your user password if sudo asks one (should be only once every 15min).

---

### Post by angkor on 2006-12-29
You can use sudo instead of su.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Edit: So slooow ;)

---

### Post by spyder0101 on 2006-12-29
that worked, thanks

---

