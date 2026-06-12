---
title: "can't boot, grub error 15"
date: 2008-05-11
forum: General Help
---

### Post by Zyphrexi on 2008-05-11
I've tried just about everything I know, and read a lot of tutorials, basically I've come to the conclusion that /boot/grub/stage1 does not exist

```
grub> find /boot/grub/stage1

Error 15: File not found
```

additional info
output of fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca4f7d63

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23175   186149856+   7  HPFS/NTFS
/dev/hdb2           23175       24322     9208832    7  HPFS/NTFS

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20448   164248528+  83  Linux
/dev/sda2           20449       48641   226460272+   5  Extended
/dev/sda5           47554       48641     8739328+  82  Linux swap / Solaris
/dev/sda6   *       20449       46465   208981489+  83  Linux
/dev/sda7           46466       47553     8739328+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 



```

it really doesn't want to reinstall grub either. I'm at my limit, if anyone can help, I'd be grateful.

EDIT: also I get a grub 15 error when trying to make a super grub disk... wtf?

---

### Post by zvacet on 2008-05-12
Did you tried [this]("http://users.bigpond.net.au/hermanzone/p15.htm#15")?

---

