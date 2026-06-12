---
title: "Gparted crashed during resize"
date: 2008-03-07
forum: General Help
---

### Post by mikeryder on 2008-03-07
I have ran a few searches on this subject but cant seem to find anything that helps so far.

I initially had a windows partition for XP on /dev/SDA1 (for exchange and AD tools etc), ubunto filesystem on /dev/SDA2 and about 20gb of free space. and a swap partition on /dev/SDA5

I have used Gparted to resize the Ubuntu partition to take up the remaining space, however the system crashed during the resize and now I get Grup error 15" when booting from hard disk. :(

I can boot up via Ubunto CD and run Gparted but this shows the merged partition /dev/SDA3 nearly empty.

I'm sure i had something similar some time last year but cant remember the resolution. might have had to manually set partition block sizes 

any ideas ?

a "sudo fdisk -l" lists all partitions (/dev/sda3 shows it's size as it should be AFTER the resize so i'm not sure how far it got)

Ubunto 7.10

---

