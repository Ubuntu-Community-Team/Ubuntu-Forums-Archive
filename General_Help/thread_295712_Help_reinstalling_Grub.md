---
title: "Help reinstalling Grub"
date: 2006-11-08
forum: General Help
---

### Post by wolf202 on 2006-11-08
Ok so I reinstalled windows and it messed grub so i'm trying to reinstall it with a live cd.  I've been trying all the methods on the master list.

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

The thing is when I type "root (hdX,X) or whatever I can never find one that works I don't know what to choose

This is the picture of my hdd setup can someone tell me what to type because find /boot/grub/stage1" does not work.

[IMG]http://img.photobucket.com/albums/v440/wolf202/a279e0b3.png[/IMG]

The **51GB partition is Windows** the **40GB partition is Ubuntu**, the others are just NTFS Data Storage

BTW, I'm using the Edgy Eft AMD64 live CD

-wolf

---

### Post by wolf202 on 2006-11-08
bump

---

### Post by wolf202 on 2006-11-08
bump again

---

### Post by LenzM on 2006-11-08
You should be able to do this
```

sudo grub-install /dev/hdb

```

---

