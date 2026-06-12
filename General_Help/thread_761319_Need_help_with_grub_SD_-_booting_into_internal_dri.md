---
title: "Need help with grub SD - booting into internal drive, partition 1"
date: 2008-04-21
forum: General Help
---

### Post by nappymonster on 2008-04-21
hi,
I've heard about grub super disk, and it looks great. GRUB has broken so many times for me, it looks like a very useful cd to have around. And when it breaks, if i don't have alot of time due to school work (stupid deadlines), i can't be wasting all of my time fixing grub. Vista is on my internal drive, and it has not been partitioned. Ubuntu is on the external hd, and has only been partitions by the installer, the way it is when you select "Use entire disk". 

So i have a few questions:

-How do i work out that vista is (hda,0,1) or whatever it is, and how do i work out what ubuntu is?
-If GRUB breaks, how do i then boot into hda 0,1, using grub super disk or anything else? I'd rather it didn't permanently remove grub, just as a one off boot into hda 0,1 without grub, for that piece of work i'll have left that i need to finish on vista.

Thanks,
Nappymonster

---

### Post by marufaberlin on 2008-04-21
try putting "(hd" into the grub command line and press tab. when you selected the right one, enter a comma and do tab again. That gives you a list.

---

### Post by nappymonster on 2008-04-21
Thanks alot, when i next reboot i'll try it. After i get this info, if GRUB breaks, how do i directly boot into hda1,0 or whatever?

Thanks,
Nappymonster

---

### Post by marufaberlin on 2008-04-22
well, if grub still works, you'll be fine. Otherwise use the supergrub CD.

Do the following commands in the grub command line (press c to enter it or p if you have a password and then c):

```

root (hd0,1)

```
if (hd0,1) is the partition you want to boot from. That tells grub which partition to use as the root partition

Then we'll load the kernel:
```

kernel /boot/vmlinuz root=/dev/hda1 ro

```
if your kernel is at /boot/vmlinuz and your root partition is at /dev/hda1.

Then (optionally, if you have a ramdisk) we'll load the rd:
```

initrd /boot/initrd

```
if your ramdisk is at /boot/initrd.

then a single command will boot (guess what it'll bee, it's not too hard :-D ):
```

boot

```

If you need any other kernel options, append them to the kernel command.

Pleased to be of service :-D.

---

### Post by adrian15 on 2008-04-24
> **nappymonster said:**
> Vista is on my internal drive, and it has not been partitioned. Ubuntu is on the external hd, and has only been partitions by the installer, the way it is when you select "Use entire disk". 


Having Linux installed in a external hard disk can be prone to errors if you have remove it and you want to boot your internal hard disk when removed.

Please check [SuperGrubDisk's Grub On Removable Hard Disk Howto](http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDisk).

adrian15

---

