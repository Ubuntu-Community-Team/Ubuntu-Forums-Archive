---
title: "ext3 parition turned Read Only"
date: 2007-02-28
forum: General Help
---

### Post by kopilo on 2007-02-28
When giving access to an ext3 parition to both windows an ubuntu (on a dual boot machine) I find that more often then not it becomes unreadable in windows and read only in ubuntu, as in it works fine and then one day it will become read only etc...

Apparently there is an easy fix for this using FS check or something but does anyone know how this problem can be resolved? (Either then using a FAT32 partition)

---

### Post by nereid on 2007-02-28
Do you mount the partition read only? What does your fstab say (if you don't mount it manually, then my point is moot)?

---

### Post by bodhi.zazen on 2007-02-28
You may have errors on the disk ...

Unmount the partition (or run from the live CD)
		
fsck -rfv /dev/hdxy

where hdxy is the shared partition.

---

### Post by kopilo on 2007-02-28
> **nereid said:**
> Do you mount the partition read only? What does your fstab say (if you don't mount it manually, then my point is moot)?
FSTAB
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5       /media/docs     ext3    user,defaults   0       0

```
No it isn't mounted as read only.

---

### Post by kopilo on 2007-02-28
> **bodhi.zazen said:**
> You may have errors on the disk ...

Unmount the partition (or run from the live CD)
		
fsck -rfv /dev/hdxy

where hdxy is the shared partition.
Thanks, I've done it on /media/docs (because that is the location of the partition). It did come up with a block error and I have choosen to let it fix it.. Just waiting to see the outcome now.

---

### Post by bodhi.zazen on 2007-02-28
> **kopilo said:**
> Thanks, I've done it on /media/docs (because that is the location of the partition). It did come up with a block error and I have choosen to let it fix it.. Just waiting to see the outcome now.

You should do this (if you have problems) :

```
sudo umount /media/docs
fsck -rfv /dev/sda5
mount /media/docs
```

You can also change the last 0 in your fstab entry to a 2 to check the file system at boot time :

> /dev/sda5       /media/docs     ext3    user,defaults   0       **2**

---

### Post by kopilo on 2007-02-28
> **bodhi.zazen said:**
> You should do this (if you have problems) :

```
sudo umount /media/docs
fsck -rfv /dev/sda5
mount /media/docs
```

You can also change the last 0 in your fstab entry to a 2 to check the file system at boot time :
Thank you so much, the drive is now readable and thank you for that extra bit of information, I shall update my fstab. =)

---

### Post by bodhi.zazen on 2007-02-28
> **kopilo said:**
> Thank you so much, the drive is now readable and thank you for that extra bit of information, I shall update my fstab. =)

You are most welcome. Glad it worked out ;)

---

