---
title: "kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2006-12-13
forum: General Help
---

### Post by GuiGuy on 2006-12-13
I was using Ubuntu 6.10 - it had been well behaved

This morning on a reboot the boot failed with 

Starting Up
[17179572.18800] RAMDISK: out of compressed data
[17179572.18800] invalid compressed format (err=1)
[17179572.18800]  kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


and that's it. Same on recovery mode. 

I realise there is a thread on this topic from a year ago. I tried some of the solutions offered but none helped, i.e. booting live from CD and 


mount /dev/hda7 /mnt/linux
chroot /mnt/linux /bin/bash
sudo mount -t proc /proc /proc
sudo apt-get install binutils
sudo apt-get install --reinstall linux-image-2.6.17-10-generic

(2.6.17-10-generic is my kernel version, I think).

I am entirely out of my depth here (noob at this level), and, of course, have not backed the box up since last week.

Any help, anyone. Or maybe I should give up on linux, because when these things happen it just seems to be too hard. :confused:

Thanks

---

### Post by GuiGuy on 2006-12-14
[QUOTE=GuiGuy;1881858]I was using Ubuntu 6.10 - it had been well behaved

This morning on a reboot the boot failed with 

Starting Up
[17179572.18800] RAMDISK: out of compressed data
[17179572.18800] invalid compressed format (err=1)
[17179572.18800]  kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
/QUOTE]

I found the solution in this thread:

[http://www.ubuntuforums.org/showthread.php?t=296809&highlight=kernel+panic](http://www.ubuntuforums.org/showthread.php?t=296809&highlight=kernel+panic) using "AgenT"'s guide to re-install the kernel.

Thanks

---

