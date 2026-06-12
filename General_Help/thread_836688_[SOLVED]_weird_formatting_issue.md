---
title: "[SOLVED] weird formatting issue"
date: 2008-06-21
forum: General Help
---

### Post by moore.bryan on 2008-06-21
i'm running hardy with openbox on a lenovo z61e with a built-in card reader and i'm trying to format the sd card fat32. i fire-up gparted, format the card fine, can read and write files to it, but when i restart the computer, the partition i created on the sd doesn't exist. what gives?

---

### Post by spiderbatdad on 2008-06-21
could you post /etc/fstab?

---

### Post by moore.bryan on 2008-06-21
i don't mount it via /etc/fstab... just manually with 
```
sudo mount -t vfat -o rw,noatime,user,umask=0 /dev/mmcblk0p1 /mnt/sd
```
after i gparted it... but the partition itself doesn't exist when i shutdown and log back in.

---

### Post by spiderbatdad on 2008-06-21
maybe umask=0000
also have you sudo mkdir /media/your_device?

---

### Post by moore.bryan on 2008-06-21
> **spiderbatdad said:**
> maybe umask=0000
unfortunately, i've tried this to no avail...
> also have you sudo mkdir /media/your_device?
i'm mounting in /mnt, not /media... do you think **that** could be destroying my partition?

---

### Post by spiderbatdad on 2008-06-21
```
dmesg | tail
```might show what is happening.

---

### Post by moore.bryan on 2008-06-21
```
dmesg | tail
```
gives nothing... like i wrote, the partition doesn't even **exist** after i've shutdown and restarted. what in the world could cause the partition to be **deleted**?

---

### Post by moore.bryan on 2008-07-07
okay, so for no good reason, it'll mount if the mount-point is in /media, but not if it's in /mnt.

whatever.

;-)

---

