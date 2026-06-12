---
title: "windows trouble with grub"
date: 2007-07-04
forum: General Help
---

### Post by rubikfreak on 2007-07-04
When I try to boot in to Windows XP Pro from grub, it says
```
Starting up ...
GRUB
```
and does nothing else.
I checked /boot/grub/menu.lst and nothing looks wrong:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
(hd0,0) is correct. Does anyone have any ideas?
Perhaps I should reinstall grub?

---

### Post by confused57 on 2007-07-05
Maybe this will help:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_)

---

