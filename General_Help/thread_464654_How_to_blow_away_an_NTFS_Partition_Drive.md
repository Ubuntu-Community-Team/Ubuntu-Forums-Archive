---
title: "How to blow away an NTFS Partition Drive"
date: 2007-06-04
forum: General Help
---

### Post by Geekkit on 2007-06-04
Hi,

Quick question. I was wondering under 7.04 how to blow away an old NTFS partition on another separate drive. It's on the primary (master) not that it matters because Ubuntu/Linux seems to be careful/honor boot records. I simply want to use the NTFS partition from XP and free it up for extra files space since I know I'm not going back.

Any help/comments/flames greatly appreciated.

---

### Post by taurus on 2007-06-04
Install gparted and use it to format that partition to whatever filesystem you want to.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
Then look in System -> Administration.

---

### Post by merlinus on 2007-06-04
Gparted works great.  If not from ubuntu, then from the live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by Geekkit on 2007-06-05
Thank you taurus, merlinus, for that prompt reply! I will do this.

:p

---

