---
title: "Help please, partition is suddenly empty"
date: 2008-06-26
forum: General Help
---

### Post by ybd on 2008-06-26
Hey,

I recently reinstalled Ubuntu on a new partition (accidentally). After using GParted to erase the partition and extend another one, and after using the Super Grub Disc (not sure which caused the problem) I now have a "blank" sda2 partition (it's an NTFS partition). It reports as blank in file explorers (Ubuntu as well as XP.

I'm saying "blank" because the drive still reports as nearly full, and with PhotoRec it looks like everything is still there, but I don't have enough space to recover to another partition. Also by messing around with mounting/unmounting I was able to get the errors in the attachment but trying to do the setuid root procedure described in ntfs-3g.org didn't seem to work (the partition it still "empty")

What can I do?

---

### Post by ybd on 2008-06-26
bump. please, I have some really important stuff in there...

---

### Post by VMC on 2008-06-26
I've neve had to use it or even install it, but there is a program called "testdisk" and here is a success story and example of installing:
[http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/](http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/)

Maybe just a simple as : apt-get install testdisk

Also can you output your drive list:

```
sudo fdisk -l
```

---

