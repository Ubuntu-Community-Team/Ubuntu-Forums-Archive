---
title: "Why am i getting ext4 buddy errors for an ext2 fs?"
date: 2017-10-10
forum: General Help
---

### Post by SJI on 2017-10-10
I've got a nas that runs 14.04.LTS. The boot drive is ext4 and data drives are ext2.
I'm seeing ext4_mb_generate_buddy:756 errors for one of the data drives even though it's ext2 and i can't figure out why that is.
```
EXT4-fs (sdb1): initial error at time 1452925488: ext4_mb_generate_buddy:756
```
from dmesg
```
[   96.923066] EXT4-fs (sdb1): mounting ext2 file system using the ext4 subsystem
[   97.002962] EXT4-fs (sdb1): warning: mounting unchecked fs, running e2fsck is recommended
[   97.013310] EXT4-fs (sdb1): mounted filesystem without journal. Opts: (null)
```
Running fsck gives the drive a clean bill of health but after a short while the buddy errors are logged again.
```
uname = Linux lithium 3.13.0-96-generic #143-Ubuntu SMP Mon Aug 29 20:15:47 UTC 2016 i686 i686 i686 GNU/Linux

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty
```
Anybody know why i'm getting ext4 errors for an ext2 fs?

SJI

---

