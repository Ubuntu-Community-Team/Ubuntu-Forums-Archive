---
title: "swap problems"
date: 2007-06-02
forum: General Help
---

### Post by funpop on 2007-06-02
i recently installed windows xp. the windows installer told me, there are too many primary partitions on my disk, so i deleted my swap partition. i know  4 primary partitions are possible, and there have only been 3 before windows installation, no idea why windows is like that ;). the installation worked fine, i was able to set up grub again, dual boot works.

kubuntu does work too, but i have now no swap available. i booted from a live cd and formatted the unallocated space into linux swap again. but somehow im not able to get this new swap working with my kubuntu system. i manually used the mkswap command and used the UUID i got for my fstab. but still when im booting (i always boot without "quiet" and "spash"), i see the FAIL when the kernel tries to activate the swap..

here is my messed up fstab:
(hdb is a sidux installation)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda2
UUID=ae14a118-f746-4b56-9776-39b3f4e85d92 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdb1
# /dev/hda4
UUID=3377e4cd-a33e-4b67-b37e-3895cb98a4fc /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda1
UUID=D4C814D3C814B628 /media/hda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda3
UUID=82479429-d6a8-46df-b32a-396bb11f783d none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
UUID=82479429-d6a8-46df-b32a-396bb11f783d  auto user,sw,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb1  auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
```

here is something from the shell:

```
michael@BlackboX:~$ sudo swapon -s
Filename                                Type            Size    Used    Priority
/dev/hda4                               partition       1028152 0       -2

sudo swapon -a
swapon: /dev/disk/by-uuid/82479429-d6a8-46df-b32a-396bb11f783d: Device or resource busy

michael@BlackboX:~$ sudo swapon /dev/hda4
swapon: /dev/hda4: Device or resource busy
```


any idea how i can fis this problem ?

---

