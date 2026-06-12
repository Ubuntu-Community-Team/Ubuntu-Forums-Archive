---
title: "[xubuntu] doesn't boot"
date: 2015-06-24
forum: General Help
---

### Post by feannor on 2015-06-24
I used to have an PC with both XP and Xubuntu. I uninstalled XP and formatted the partition. But now, I can't anymore access to the Linux OS. I tried to change some setting with Gparted (on the HBCD USB key), but nothing changed.
I've got always the same message: ```
Non-system disk or disk error, replace and strike any key when ready
```

For the moment I've got 2 partition: the Linux-one (ext4) and one just for store some files (FAT32). And then I've got aso 30GB not allocated (the old windows partition).

Does someone have some advice to give me ?

---

### Post by Bucky Ball on 2015-06-24
Welcome. Boot Repair is your friend. :)

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

You can also try re-installing grub from live media (Ubuntu install disk) by opening a terminal and:

```
sudo grub-install /dev/sda
```

PS: Please use default font and size. Extra large or bolder font is equivalent to shouting. I have edited your last post. :)

---

### Post by VMC on 2015-06-24
Bring up a Terminal(Ctrl+Alt+t) and type the following ```
sudo blkid
``` so we can see what partitions you have installed.

---

