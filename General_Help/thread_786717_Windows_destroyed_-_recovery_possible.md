---
title: "Windows destroyed - recovery possible?"
date: 2008-05-08
forum: General Help
---

### Post by gambiting on 2008-05-08
Hello! I have a very big problem. I wanted to format my pendrive using fdisk(I mean linux one) and accidentialy I have formated my windows hard drive. Nothing was written so far on it,so my question is - is there any way to recover lost partitions? Things I have done:

fdisk /dev/sdd1 (I thought it's my pendrive,but it was my windows hdd)
(inside fdisk):
d - I deleted both partitions
n - created new one
enter for deafult(biggest size)
t - changed filesystem type to Fat32
and then w - write changes to disk.

After that I did:
mkfs.vfat /dev/sdd1

before I had two partitions,one 30GB,and second 50GB,both NTFS formated.
As far as I understand only really dangerous thing I did was creating a filesystem on this new partition. Any ideas how to undo it? Please help :D

---

### Post by tamoneya on 2008-05-08
you shoudl still be recoverable.  You should go download [RIPLinux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/").  THis is a liveCD that is packaged with several data recovery tools.  The one you should use is testDisk.  It will search your disks for partitions instead of just looking at the head of the disk for all the partition information.  Then you can copy the data on to some sort of external drive.

---

### Post by gambiting on 2008-05-08
> **tamoneya said:**
> you shoudl still be recoverable.  You should go download [RIPLinux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/").  THis is a liveCD that is packaged with several data recovery tools.  The one you should use is testDisk.  It will search your disks for partitions instead of just looking at the head of the disk for all the partition information.  Then you can copy the data on to some sort of external drive.

Ok,thanks for the info,I will try it for sure,but is there any way to just recover the old partition table without reinstalling windows?

---

### Post by tamoneya on 2008-05-08
this is not going to install windows at all.  It wont change the data on your harddisk at all.  This will meerly help you extract the data.  Then once you have done that you can then format the drive in question for whatever OS you like.

---

### Post by aysiu on 2008-05-08
If the partition table itself is unrecoverable (you should try to recover it, though), you can also use *photorec* to recover your important data. That may be available on RIPLinux, too.

---

### Post by gambiting on 2008-05-08
> **aysiu said:**
> If the partition table itself is unrecoverable (you should try to recover it, though), you can also use *photorec* to recover your important data. That may be available on RIPLinux, too.
I don't need to recover any important data(ok,maybe few files),I'm asking if it's possible to revert to previous state with few simple steps(like recovering partition table so windows will ba able to boot again). I will try this riplinux in a few minutes and I will see what features it has.

---

