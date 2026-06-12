---
title: "Trouble booting after Gparted repartioning"
date: 2008-03-08
forum: General Help
---

### Post by nomexous on 2008-03-08
About 2 weeks ago, I became one of the unlucky few to be affected by the infinite bluescreen-reboot loop caused by the Vista SP1 prerequisite update. So, with my Gusty livecd, I rescued my files and attempted to reinstall Vista. Unfortunately, Vista refused to cooperate, so I just installed Ubuntu, leaving Vista in its place, in case I needed files from it.

Last night, I determined that I no longer needed Vista, and decided to nuke it. Using my Gparted CD, I deleted sda1 (the broken Vista install), sda2 (a second partition that I created when installing Vista), and expanded sda3 (Ubuntu Gusty) all the way to the left to fill up the empty space. I left Gparted to do its thing, and went to study psychology, leaving the lid of my laptop down. When I left it, it had been copying files (presumably moving the partition to the left). But when I came back, the screen was blank except for the cursor (in the shape of an X). The touchpad wouldn't move it at all. I was confused, so I pressed the power button once (didn't hold it down), and the computer restarted.

Upon booting, I was presented with the familiar Grub bootloader, and proceeded to boot the Ubuntu install. The loading screen appeared, but the progress bar didn't even advance half a block before it stopped. After a few seconds it disappears, and I get something similar to:
```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)_
```It appears to be a terminal, but it can't do anything useful. Running "ls -a" reveals no home folder, which I guess means that my Ubuntu partition isn't mounted. I tried to run e2fsck to repair the disk, but it had no effect other than finding a few orphaned files and fixing them.

So, apparently, the Gparted repartitioning broke my Ubuntu install. I can still access my files on the broken Ubuntu install by using the livecd (thank goodness). Can anyone shed some light on how to fix this? Thanks in advance.

---

### Post by ssj3strife on 2008-03-08
In the grub menu, try editing the default boot option just before booting. You need to remove all instances of the word "quiet" and "splash" so you can see what's going on during the boot. See if it generates a coherent error message you can post here.

Also, once you get dropped to the busybox shell, run these:
ls /dev | grep hd
ls /dev | grep sd
and post the results here.

---

