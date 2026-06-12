---
title: "GRUB loader"
date: 2007-01-03
forum: General Help
---

### Post by kusal on 2007-01-03
How to set windox xp as default selection in boot loader

thnx

---

### Post by pay on 2007-01-03
I think that you just have to edit the file /boot/grub/menu.lst with default         X, where is the number of the listing that you want to boot starting from zero. But I maybe wrong so back up the file first```
sudo cp /boot/grub/menu.lst /boot/grub/menu.list_bak
```

---

### Post by DMAthlon on 2007-01-03
i had a HUGE LONG article practically prepared on how to do it. but then cut it, forgot and done lost the clipboard data!!!!!!!!!!!


here's short and sweet:

First: in terminal
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
(makes backup, jsut delete "_backup" from teh filename to restore it.

Second: in terminal
```
sudo gedit /boot/grub/menu.lst 
```

in most cases searching for 
```
default		0
```
and replacing the 0 with a 6 will work. so just replace them, save the file and restart. windows xp should now be the highlighted option,

if that doesn't work, the follow the _**1. Conventional Method**_ in this [here]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") reading.


if you read it enough, you'll get it, trust me.

happy linuxing.

---

