---
title: "Completely removing ntfs partitions"
date: 2007-12-21
forum: General Help
---

### Post by nils234 on 2007-12-21
Hey,

I currently dual boot between xp and ubuntu, this works fine. I use ubuntu 99 percent of the time but I still have windows for games only. There is one big annoyance though, the ntfs partition is still there in ubuntu. I edited fstab so that they don't show up on the desktop, but when I go to ( for example ) Places>Computer, the partition is there. I don't know why, but it annoys me :) I want those 2 to be completely separated, imagine how ashamed I would be if someone found out I actualy run windows :P

No but realy, does anybody know how to do this? Maybe totaly rule out ntfs support? ( if so, how ).

Thanks in advance,

Nils

---

### Post by taurus on 2007-12-21
You mean you don't want to mount that ntfs partition?  Maybe you need to edit /etc/fstab and place a # in front of the entry for your ntfs partition to comment it out so it won't be mounted automatically each time you boot Ubuntu.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by nils234 on 2007-12-21
Allready done that, so they're not mounted. However, at places>computer the ntfs partition is still shown. When I click it it asks me to mount it first. I don't want that, I want it completely gone.

---

### Post by nils234 on 2007-12-23
Maybe the best way would be to completely remove ntfs support, is this possible?

---

