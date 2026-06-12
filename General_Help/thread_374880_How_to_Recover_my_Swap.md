---
title: "How to Recover my Swap???"
date: 2007-03-03
forum: General Help
---

### Post by true_friend on 2007-03-03
Hi  folks
i have lost my swap partition when i boot my system it says 
Activating Swap (fail)
due to this my system is slowed down i am using kubuntu edgy upgraded from dapper.
is there any solution??
Regards
True_Friend

---

### Post by Kateikyoushi on 2007-03-03
Could you post the output of these commands ?

> cat /etc/fstab
fdisk -l

---

### Post by true_friend on 2007-03-03
not currently at my system but i post it later today
thnx for reply

---

### Post by true_friend on 2007-03-03
This is the out put of cat /etc/fstab
....................................................................
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda6 -- converted during upgrade to edgy
/dev/hda6 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1 -- converted during upgrade to edgy
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000,loop,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5 /media/hda5 vfat iocharset=utf8,umask=000,loop,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/hda8 -- converted during upgrade to edgy
/dev/hda8 /media/hda8 vfat iocharset=utf8,umask=000,loop,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/hda9 -- converted during upgrade to edgy
/dev/hda9 /media/hda9 vfat iocharset=utf8,umask=000,loop,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/hda7 -- converted during upgrade to edgy
/dev/hda7 none swap sw 0 0
...........................................................................
output of 2nd one
--------------------------------------
Disk /dev/hda: 41.1 GB, 41110142976 bytes
240 heads, 63 sectors/track, 5310 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1355    10243768+   c  W95 FAT32 (LBA)
/dev/hda2            1356        5309    29886570+   f  W95 Ext'd (LBA)
/dev/hda5            1356        1775     3169530    b  W95 FAT32
/dev/hda6            1776        2589     6144831   83  Linux
/dev/hda7            2589        2710      915673+  82  Linux swap / Solaris
/dev/hda8            2711        4064    10236208+   b  W95 FAT32
/dev/hda9   *        4065        5309     9412168+   b  W95 FAT32
.......................................................
Regards

---

### Post by Kateikyoushi on 2007-03-03
Try this.

```
sudo swapon -a
```

---

### Post by true_friend on 2007-03-03
out put
.................
swapon: /dev/hda7: Invalid argument
................
reformatting of swap can solve this?

---

### Post by Kateikyoushi on 2007-03-03
I do not think so, the invalid arguement could refer to the fstab but that seems to be correct.

I looked around and people recommended the following.
```
mkswap /dev/hda7
swapon -a
```

---

### Post by true_friend on 2007-03-03
The result
ss@ss-desktop:~$ mkswap /dev/hda7
/dev/hda7: Permission denied
ss@ss-desktop:~$ sudo mkswap /dev/hda7
Password:
Setting up swapspace version 1, size = 937644 kB
no label, UUID=3acf2264-147b-4c33-84b3-1b4de71753ed
ss@ss-desktop:~$ sudo swapon -a
ss@ss-desktop:~$

i think it should be ok but i inform after restarting not now later currently going for my duty
Thnx for reply
Regards
True_Friend

---

### Post by Kateikyoushi on 2007-03-03
Yes you are right I forgot the sudo, as I see it changes the fstab as well, now should work.

---

### Post by true_friend on 2007-03-03
It is ok now.

---

