---
title: "W95 FAT32 mount trouble"
date: 2008-07-07
forum: General Help
---

### Post by PaiPimenta on 2008-07-07
Dear Ubuntu Community,

     Help!  I use fdisk to clear and install a single, full disk sized partition on an external /dev/sda, creating /dev/sda1, type W95 FAT32 (hex code "b") in order to transfer the data from one of my /dev/hdb partitions to this external drive (data being all my old windows xp laptop files).

     Despite the trouble I'll have of restoring this old xp system, I am not able to mount the external hard drive, I think due to a filesystem something.

     I formatted the disk on my Mac iBookG4 running 10.3.9 with Disk Utility as an MS-DOS filesystem, and was able to mount and copy the data..... with eightand.thr filenames!!! (8.3, old school msdos)

   Man, what do I do??  I want to reformat and reinstall Xubuntu, replacing my command line only ubuntu, which is probably why the X gui is having problems despite fully installing past the 6% software install cut-off bug.

Any help with a filesystem suggestion/mount commands?

Here's what I've done:

     sudo mount -t vfat /dev/sda1 /mnt/VieO

typical wrong file system mount message...

Pepper
aka PaiPimenta

---

