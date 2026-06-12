---
title: "Grub, remove partition selection screen?"
date: 2007-10-17
forum: General Help
---

### Post by jtreach on 2007-10-17
I recently removed my Windows partition to migrate to Ubuntu permanently! :)

Only problem is the grub partition selection screen which still comes up. What's the easiest way to remove this?

Thanks in advance.

---

### Post by aidanr on 2007-10-17
In a terminal:
```
gksudo gedit /boot/grub/menu.lst
```
and remove the # from #hiddenmenu

---

### Post by jtreach on 2007-10-17
Such a fast and helpful response! Thanks! :D

---

