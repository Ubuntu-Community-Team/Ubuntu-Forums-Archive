---
title: "NTFS lock-ups"
date: 2007-12-17
forum: General Help
---

### Post by mic159 on 2007-12-17
Is there a way to stop Ubuntu locking up everytime i write to an NTFS partition?

My particular partition is 200GB and every time i write to it, the whole of ubuntu locks up for 1-2 minutes after writing large (100MB - 1GB) files to it.

Is this a common problem? is there a fix?

This is a problem as i use that partition as media storage.

---

### Post by wjp.reg on 2007-12-17
can you post the output for the following terminal command:

```
fdisk -l
```

---

### Post by mic159 on 2007-12-18
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9ede9ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       30401   213479752+   f  W95 Ext'd (LBA)
/dev/sda5            3825       29320   204796588+   7  HPFS/NTFS
/dev/sda6           30340       30401      497983+  82  Linux swap / Solaris
/dev/sda7           29321       30339     8185086   83  Linux

Partition table entries are not in disk order

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bb5be22

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24321   195358401    7  HPFS/NTFS
```

the partition i was writing to was /dev/sda5

---

### Post by kpkeerthi on 2007-12-18
```

Is this a common problem?

```
No. I found it to be very stable with writing large files. I have my backups in a NTFS partition.

Install **ntfsprogs** from synaptic and run
```

ntfsfix /dev/sda5

```

Not sure but it may help.

---

### Post by mic159 on 2007-12-18
still locking up...

it sometimes corrupts the files its writing, or just stops and gives an I/O error

and i found this in /var/log/daemon.log
```
Dec 18 20:17:17 Server ntfs-3g[4042]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Dec 18 20:17:17 Server ntfs-3g[4042]: ntfs_attr_pread partial write (147292160: 4096 <> -1): Input/output error
```
its in there heaps of times

any other thoughts?

---

### Post by kpkeerthi on 2007-12-18
Did you try running **chkdsk /R** with windows recovery disk? It will take a while for the whole operation to finish.

---

### Post by mic159 on 2007-12-19
can i just do a scandisk inside windows?

---

### Post by szaka on 2007-12-19
> **mic159 said:**
> 
and i found this in /var/log/daemon.log
```
Dec 18 20:17:17 Server ntfs-3g[4042]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Dec 18 20:17:17 Server ntfs-3g[4042]: ntfs_attr_pread partial write (147292160: 4096 <> -1): Input/output error
```

Recent Linux kernels indeed have a problem which can cause old NTFS-3G releases to hang up: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

Upgrade NTFS-3G and if the problem goes away then submit an Ubuntu bug report.

---

### Post by mic159 on 2007-12-19
> **szaka said:**
> Upgrade NTFS-3G and if the problem goes away

How can i upgrade it? :S because synaptic says its at the latest version. do i have to manually install the latest version?

---

### Post by mic159 on 2007-12-20
ummm now the whole system is completly stuffed.. GRUB wont even load.. gives error 15.

all i did was update the kernal (auto updates did it)

does that mean its time for a new HDD?

---

### Post by mic159 on 2008-01-14
FYI this problem has been solved. It was a hardware problem, the PSU was inadequate, replaced it with a $70 550W PSU and i havnt had a problem with it since.

---

