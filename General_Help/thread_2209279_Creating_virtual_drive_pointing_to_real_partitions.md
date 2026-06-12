---
title: "Creating virtual drive pointing to real partitions sector mismatch"
date: 2014-03-04
forum: General Help
---

### Post by lildigiman on 2014-03-04
I'm trying to complete a walk-through as linked here: [http://fds-team.de/cms/articles/2013-12/use-a-real-windows-7-partition-in-virtualbox-kvm-vmware-player-u.html](http://fds-team.de/cms/articles/2013-12/use-a-real-windows-7-partition-in-virtualbox-kvm-vmware-player-u.html)

I am able to create the boot.mgr file and attach it to /dev/loop0. After that:


When I create the virtual disk, my sectors from my raw hard drive and the virtual disk mismatch. The article doesn't mention anything about what to do in that circumstance (as if it shouldn't happen?)


```

XXXXX$ sudo mdadm --build /dev/md7 --level=linear --raid-devices=3 /dev/loop0 /dev/sdd1 /dev/sdd2
mdadm: array /dev/md7 built and started.
XXXXX$ sudo fdisk -l /dev/md7


Disk /dev/md7: 500.1 GB, 500105347072 bytes
2 heads, 4 sectors/track, 122096032 cylinders, total 976768256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md7 doesn't contain a valid partition table
XXXXX$ sudo fdisk -l /dev/sdd


Disk /dev/sdd: 500.1 GB, 500107862016 bytes
224 heads, 19 sectors/track, 229504 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x818a9b64


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdd2          206848   976768344   488280748+   7  HPFS/NTFS/exFAT

```


At this point, you can see that my total bytes for my raw disk (sdd) is 500107862016 bytes and the virtual disk (md7) is 500105347072 bytes, a difference of 2514944 bytes.


The first partition being created in fdisk works fine, however if I try to create the second partition in fdisk I get the error "value out of range" because the virtual drive has less sectors as a result of the mismatch listed above.


Does anyone know why I'm getting this mismatch and what there is I can do to fix it?


Thanks in advance.

---

