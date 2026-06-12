---
title: "Freeze up when trying to mount a raid 0 partition"
date: 2008-04-24
forum: General Help
---

### Post by cloudeen on 2008-04-24
I have a winxp 64bit in 160gx2 raid 0 setup. After facing problem boot into windows i relise it is a hdd failure and trying to recoer my data using ubuntu.

Booting up ubuntu 64bit and install dmraid, i can see the partition in /dev/mapper. But when i try to mount the first ntfs partition of the raid0 setup, ubuntu will freeze up.
I can mount the 2nd partition and copy out some files, but when i try to access certain other folder, ubuntu freeze up as well.
(the longest i have wait was 10hrs, should i wait longer?)

I tried "ddrescue /dev/mapper/nvidia_xxxx /media/disk" for the 1st partition, ddrescue freeze up as well after copying 1g of the image.

Is there any other magic tools/command which i can try to access/mount these partition?

Please help! Thanks.

---

