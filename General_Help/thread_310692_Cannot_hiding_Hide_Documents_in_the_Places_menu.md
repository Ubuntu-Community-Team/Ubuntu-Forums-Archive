---
title: "Cannot hiding Hide Documents in the Places menu"
date: 2006-12-01
forum: General Help
---

### Post by L3oN on 2006-12-01
Hi,
sorry for my poor english...

I've some problems to hide Recent Documents in the Places menu...

I tried this: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s06.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s06.html)
But not take effect...

Can you help me ?

---

### Post by tzulberti on 2006-12-01
You should take into account two things:
1) You should run the command as the user, not as root
2) You must log out, so this take effect

---

### Post by L3oN on 2006-12-01
The command i ran as user, but don't work... so i tried as root, but nothing too...

I logout 100 times, nothing..

I've these files in my home (each with chmod 400):
```
l3on@SubMission:~$ ls -a |grep rece
.recently-used
.recently-used.xbel

```

---

### Post by L3oN on 2006-12-02
I don't understand why it's not work...

This is my situation:
```
l3on@SubMission:~$ ls -al |grep rece
-r--------  1 l3on l3on      3019 2006-12-01 16:06 .recently-used
-r--------  1 l3on l3on     23096 2006-12-01 23:19 .recently-used.xbel

```
But in menu "Recent Documents" is already able !!

---

### Post by L3oN on 2006-12-04
None can help me?

---

### Post by malcolm1234 on 2006-12-17
> **L3oN said:**
> None can help me?

[http://ubuntuforums.org/showthread.php?p=1767264](http://ubuntuforums.org/showthread.php?p=1767264) has a solution of sorts

---

