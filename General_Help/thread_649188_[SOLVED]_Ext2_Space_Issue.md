---
title: "[SOLVED] Ext2 Space Issue"
date: 2007-12-24
forum: General Help
---

### Post by jediborger on 2007-12-24
I'm currently creating a bootable usb stick for several OS's. I wish to use ext2 so I can utilize symlinks as fat partitions can't handle them. But I'm wondering if anyone knows why for example when I create an ext2 partition that is 710 mb, 36 mb is magically used by something. But if I change the partition to fat32 I can use the full space. Why does ext2 use 36 mb of the partition? I could make the partition larger as a work-around but then that's wasted space. I don't need journaling or fsck which I believe I've turned off. Any ideas?

---

### Post by taurus on 2007-12-24
Are you sure you use ext2 not ext3 because 5% of your disk space, 36MB for 710MB, is reserved if you are using ext3?

---

### Post by jediborger on 2007-12-24
According to both Gparted and Cfdisk, it's ext2, not ext3. Does ext2 also save a certain amount of space to prevent OS issues with lack of hd space? I plan on using this for read-only files so nothing will be written to this partition. Maybe there's a way to turn this feature off? Something in ext2fsprogs?

---

### Post by logos34 on 2007-12-24
> **jediborger said:**
> According to both Gparted and Cfdisk, it's ext2, not ext3. Does ext2 also save a certain amount of space to prevent OS issues with lack of hd space? I plan on using this for read-only files so nothing will be written to this partition. Maybe there's a way to turn this feature off? Something in ext2fsprogs?

yeah, good question.  Taurus is right--by default ext3 format reserves 5% space for root.  So it only shows as 95% available space to users.

I know how to set it to 0% during install using the text-mode installer cd.  But how do you do it like in gparted or mkfs?

---

### Post by jediborger on 2007-12-24
I really should spend more time digging into documentation before posting for help. Ext2 also reserves 5% of the drive space for "runtime processes." The space reserve can be turned off with:
```
sudo tune2fs -m 0 /dev/xxx
```

---

### Post by logos34 on 2007-12-24
And here's what the man page for mkfs.ext3 says ('-m option'):

> -**m** reserved-blocks-percentage
              Specify the percentage of the filesystem blocks reserved for the super-user.   This  avoids  fragmentation,
              and  allows  root-owned daemons, such as syslogd(8), to continue to function correctly after non-privileged
              processes are prevented from writing to the filesystem.  The default percentage is 5%.


At least you're post helped me learn something new today.

---

