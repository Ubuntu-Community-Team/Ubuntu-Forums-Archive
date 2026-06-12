---
title: "Partition type listed wrong"
date: 2013-10-21
forum: General Help
---

### Post by BKk64bp on 2013-10-21
Hello,
I have an estrange behavior in my Ubuntu server 11.04.
My VPS sda1 type is _Linux_ using fdisk AND _Swap_ using blkid commands.
The system was unstable and I have setup a new swap file because sda1 is not mounting.
Here the results:
 # fdisk -l
Disk /dev/sda: 32.2 GB, 32212254720 bytes
255 heads, 63 sectors/track, 3916 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000678c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          61      488281   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              61        3917    30968022+  83  Linux

_NOW WITH blkid COMMAND:_

   # blkid -o list
device                                     fs_type        label           mount point                                    UUID
-------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                  swap                           (not mounted)                                  
/dev/sda2                                  ext4                           /                                              466bea31-9428-415e-aaa3-2c2f3cd7c2f5

Any advise on any other issues this could cause or how to fix it without wiping the disk?
P Braconnot

---

### Post by Bucky Ball on 2013-10-21
Just a note: 11.04 is no longer supported (hasn't been for over a year) and you should be using a supported release for a server that is online. You are not getting any security updates. 

LTS releases are intended for servers and production machines. I would suggest you install 12.04. Good luck.

---

