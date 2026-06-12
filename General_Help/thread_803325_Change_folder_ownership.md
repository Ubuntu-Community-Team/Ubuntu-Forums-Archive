---
title: "Change folder ownership"
date: 2008-05-22
forum: General Help
---

### Post by itix on 2008-05-22
I have this folder on my external hard drive that is the home folder of my openSUSE-partition. I'd like to have that set to read and write permissions for "everyone", meaning basically that both my openSUSE user and my Ubuntu user can read and write to it. Is that possible?

Also, if you possibly would know anything about mounting, [this]("http://ubuntuforums.org/showthread.php?t=798471") problem still exist.

Thanx!

---

### Post by rune0077 on 2008-05-22
Press alt+F2, then type:

```
gksu nautilus
```

This opens nautilus in "root"-mode. Then browse to the folder in question, right-click it, select properties, and change the permissions to what you want.

---

### Post by itix on 2008-05-22
Great, thanx! =D

---

