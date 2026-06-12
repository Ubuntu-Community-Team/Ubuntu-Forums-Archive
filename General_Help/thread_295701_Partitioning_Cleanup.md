---
title: "Partitioning Cleanup?"
date: 2006-11-08
forum: General Help
---

### Post by dothedorky on 2006-11-08
To start off, this is my output from **sudo f-disk l**

[B]Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        3787    15060937+   f  W95 Ext'd (LBA)
/dev/hda3            3788        4865     8659035   83  Linux
/dev/hda5            1913        3736    14651248+   b  W95 FAT32
/dev/hda6            3737        3787      409626   82  Linux swap / Solaris[/B]

My question is, is there a way to clean up my /dev configurations so it goes in consistence with 1,2,3,4,5,6? Do i even NEED this many partitions? . I'm doing a dual boot with windows (even though i rarely use windows-- I kind of want to make the partition for windows smaller..) I've done partitioning once before, and this time it turns out looking like a mess. .

Also, do i *need* to have a FAT32 file? Why did ubuntu's partion helper on first install suggest this?

Thanks in Advance.

---

### Post by hexion on 2006-11-08
First of all, your partition numbers are correct.
fdisk -l doesn't show /dev/hda4 because it's a logical "contanier" partition that contains /dev/hda5 and /dev/hda6. In fact, /dev/hda5 and /dev/hda6 are logic partitions, they aren't in your MBR. This is because you only can have 4 partitions in the MBR.

You don't need 5 partitions. If you want to boot ubuntu & windows, you only need 2 as a mandatory. One for each OS. You can get rid of all other partitions, even the swap one (since Linux can run without swap but it's not recommended).

Maybe the installer suggest you having a Fat32 partition to share your files between linux and windows, since by default you cannot write a ntf partition (at least not with security) in linux.

Just curiosity, what's the problem with your partitions? I have much more than yours and have no problem at all ^^

---

### Post by dothedorky on 2006-11-20
No problem, persay, with the partitions... it just looks awfully cluttered for me. Personal preference, I suppose. Thanks for your reply, I suppose I can live:)

---

