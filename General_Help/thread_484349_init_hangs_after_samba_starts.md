---
title: "init hangs after samba starts"
date: 2007-06-25
forum: General Help
---

### Post by Portable_Jim on 2007-06-25
Suddenly my computer (Ubuntu Feisty running KDE) stopped booting, with init showing 
```
starting samba                                         [OK]
   
```It is after it starts rc.local. I can get the the other terminals however kdm has started and the GUI is not showing

Does anyone know how to help me?

(I am writing this on windows so I am very vague about details. I can however boot into ubuntu to follow instructions)

---

### Post by Portable_Jim on 2007-07-11
> **Portable_Jim said:**
> Suddenly my computer (Ubuntu Feisty running KDE) stopped booting, with init showing 
```
starting samba                                         [OK]
   
```
It is after it starts rc.local. I can get the the other terminals however kdm has started and the GUI is not showing

Does anyone know how to help me?

(I am writing this on windows so I am very vague about details. I can however boot into ubuntu to follow instructions)
Fixed: Had configured /etc/X11/xorg.conf earlier in session, so restoring the xorg.conf from the backup (yes I did make one) made everything return to normal.

---

