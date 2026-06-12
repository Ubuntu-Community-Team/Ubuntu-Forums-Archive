---
title: "Windows Paritions don't show (often)"
date: 2008-05-08
forum: General Help
---

### Post by MadnessRed on 2008-05-08
Hi, I have a very weird problem, well maybe its not that weird but I find it both unexplainable and annoying, but hey.

I can't always view my Windows partitions in Ubuntu. However sometimes I can,  week ago I was happily using Linux, running my programs installed on the windows partition and listening to my music on my windows Partition.

I have 4 partitions.

Windows
DATA
Filesystem
Swap

Or as Windows knows them C:\ D:\ U:\ Z:\

Windows has Windows XP Home installed on it, it is formatted as NTFS, size 40gb

DATA is the parition I want both OS's to access, I formatted it as FAT32 however at some point Windows managed to make it into an NTFS partiton without asking me (no data was lost so this seems very od to me)

Filesystem is the Linux Partition, 40gb again formatted as EXT3, I have an EXT viewing installed, sometime I can view this Hard Drive in Windows all the time, but usually it just says its not formatted.

SWAP - The swap partition.

SO my question. How can I get Ubuntu to view my NTFS file systems? I have 7.10 atm, and 8.10 is being sent.

And secondly, why can I view it sometimes but not all the time?

---

### Post by tamoneya on 2008-05-08
this is because the filesystems need to be mounted.  You can mount them when you need them with the following terminal command.```
sudo mount -t ntfs /dev/sda1 /mywindwows/directory
```If however you want to mount them automatically you need to add this line to the end of /etc/fstab```
/dev/sda1 /mywindows/directory ntfs defaults 0 0
``` If you dont know which device your windows drive is (the dev/sda1 part) post the result of ```
sudo fdisk -l
``` and we will explain it.

---

### Post by MadnessRed on 2008-05-08
ok, i dont have internet on ubuntu. but from memory

DATA is SDA5
Windows is SDA1

I'll try mounting them

---

