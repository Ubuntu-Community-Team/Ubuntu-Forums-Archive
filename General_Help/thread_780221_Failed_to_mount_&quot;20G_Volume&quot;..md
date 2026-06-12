---
title: "Failed to mount &quot;20G Volume&quot;."
date: 2008-05-03
forum: General Help
---

### Post by cheaptrick on 2008-05-03
hi there, i'm unable to mount my 20g partition after a fresh install of xubuntu hardy.

this is the error message when partition editor tries to mount it 

"Failed to mount "20G Volume".
org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result)."

strangely, this 20g partition seems to mount just fine on puppy linux.

---

### Post by MattBD on 2008-05-03
Can you run the following to show the partitions you have?
```
sudo fdisk -l
```

---

### Post by cheaptrick on 2008-05-03
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbacebace

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2224    17864248+  83  Linux
/dev/sda2            2225        4865    21213832+   f  W95 Ext'd (LBA)
/dev/sda5            2328        4865    20386485    c  W95 FAT32 (LBA)
/dev/sda6            2225        2327      827284+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by cheaptrick on 2008-05-03
help anyone?

---

### Post by cheaptrick on 2008-05-08
well, i'm only able mount this 20g volume if i log in as root user and run gnome parted. It wasnt like this back in gutsy..

---

### Post by kpkeerthi on 2008-05-08
Are you trying to mount /dev/sda5 ?

---

### Post by kpkeerthi on 2008-05-08
> **cheaptrick said:**
> hi there, i'm unable to mount my 20g partition after a fresh install of xubuntu hardy.

this is the error message when partition editor tries to mount it 

"Failed to mount "20G Volume".
org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result)."

strangely, this 20g partition seems to mount just fine on puppy linux.

What command did you use when this happenned?

---

### Post by cheaptrick on 2008-05-09
the error message came up when i run gnome parted.
the partition wasnt mounted automatically..

---

### Post by cheaptrick on 2008-05-14
help any one?

---

### Post by cheaptrick on 2008-05-16
any help?

---

### Post by fregl on 2009-01-08
see [http://ubuntuforums.org/showthread.php?t=772283](http://ubuntuforums.org/showthread.php?t=772283)

---

