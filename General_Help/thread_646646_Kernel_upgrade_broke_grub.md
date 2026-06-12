---
title: "Kernel upgrade broke grub"
date: 2007-12-21
forum: General Help
---

### Post by radicaledward on 2007-12-21
Okay, after some strange events, grub is broken. First, I had to reboot (into windows)  because ubuntu froze on a screensaver. After realizing I had to boot into ubuntu again to fix the partition so my windows driver could read it (If you shut down abnormally in ubuntu, some flag is set and the windows driver won't read/write/anything). Ubuntu asked if it could update the kernel, so it did. Upon rebooting, grub was utterly broken.

My menu.lst:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-13-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro single
initrd		/boot/initrd.img-2.6.22-13-generic

title		Ubuntu 7.10, kernel 2.6.22-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu 7.10, kernel 2.6.22-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=5024b6dc-b1ba-4f03-8bfc-11e0ca5a5ab5 ro single
initrd		/boot/initrd.img-2.6.22-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

All these files exist, but none of the grub entries work and none of them are the most recent version of the kernel. Any help is appreciated!

---

### Post by Pumalite on 2007-12-21
Post:
uname -a

---

### Post by tgilber1 on 2007-12-21
Try the following steps:

1.  Reboot computer
2.  Hit ESC key when GRUB menu appears
3.  Type 'c' key to get to grub menu
4.  Type "root (hd" - type only what enclosed in quotes - omit quotations
5.  Depress tab key to show available disc - you should see hd0 and up - if you have multiple disks
6.  Type "root (hd0," to view available partitions
7.  When you finish the command, it should look like "root (hdx, y)" ex. root (hd0,0) where x=the disk# and y= the partition# - Depress Enter key after typing command
8.  Type "kernel /", then tab to view filenames - you should see the contents of boot directory where image files reside.  If not, try another disk or partition
9.  Once you find the partition with the image files, select the image file of choice
10.  Type "initrd/" and tab to view initrd file
11.  Type boot and hit ENTER key

Brief example summary of GRUB commands

1.  root (hd0,0) <enter>
2.  kernel /vmlimuz-kernel-version <enter>
3.  initrd /initrd.img-kernel-version <enter>
4.  boot <enter>

If everything boots up, the update the /boot/grub/menu.lst with the correct version kernel and intitrd image files.  An alternative is to sudo apt-get install --reinstall <kernel version>

---

