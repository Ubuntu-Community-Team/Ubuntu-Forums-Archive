---
title: "Recover deleted files EXT4"
date: 2018-06-05
forum: General Help
---

### Post by bar12 on 2018-06-05
Hi, 
I made a mistake, and rsynced with --delete
I would like to recover those files, but testdisk and ext4magic show the files as 0 bytes....are the files gone?am i doing something wrong?what else can i try?

thanks!\BAr1!

---

### Post by VMC on 2018-06-05
I've never had a zero outcome. Show us your the messages that you used.

---

### Post by bar12 on 2018-06-05
thanks for the quick reply.

testdisk /dev/vda1
8TB (could that be the problem?) drive found.

proceed, Hint: None partition table type has been detected., Disk /dev/vda1 - 8001 GB / 7452 GiB - CHS 15504018 16 63

     Partition                  Start        End    Size in sectors
>   P ext4                     0   0  1 15504018  14 61 15628051087 [8TB]

 List

can see the files,, but...

 drwxrwsrwx     0   100         0  5-Jun-2018 06:53 Krugar - Xmas ride
 -rw-rw-rw-     0   100         0  5-Jun-2018 06:54 Freedom Ride.m2ts
 drwxrwsrwx     0   100         0  5-Jun-2018 06:53 Lesotho - May17

All files are showing 0 size?
do i need to do something with superblock?

thanks!!

---

### Post by bar12 on 2018-06-05
ext4                     0   0  1 15504018  14 54 15628051080 [8TB]
superblock 0, blocksize=4096 [8TB]
superblock 32768, blocksize=4096 [8TB]
superblock 98304, blocksize=4096 [8TB]
superblock 163840, blocksize=4096 [8TB]
superblock 229376, blocksize=4096 [8TB]
superblock 294912, blocksize=4096 [8TB]
superblock 819200, blocksize=4096 [8TB]
superblock 884736, blocksize=4096 [8TB]
superblock 1605632, blocksize=4096 [8TB]
superblock 2654208, blocksize=4096 [8TB]


To repair the filesystem using alternate superblock, run
fsck.ext4 -p -b superblock -B blocksize device

do i need to repair the superblock?

---

