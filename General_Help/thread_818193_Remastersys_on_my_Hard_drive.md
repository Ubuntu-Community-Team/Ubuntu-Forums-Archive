---
title: "Remastersys on my Hard drive"
date: 2008-06-04
forum: General Help
---

### Post by seanhvw on 2008-06-04
Installed Remastersys on Mardy Heron last night, just to make a fallback backup of my machine just in case. Ran the gui interface to make a personal iso. It ran for about 20 minutes then locked up, unable to use the keyboard I cut power and restarted. Now in GRUB I have another Ubuntu partition and when I login my mouse stops working and there is an install icon on the desktop. I'm guessing that Remastersys dropped the install to my hard drive and now I'm booting off of it. Would the remedy be as simple as logging into my original partition and used Gparted to remove the one I created?

Sean :)

---

### Post by VMC on 2008-06-04
I haven't used remaster on ubuntu. Was thee any indication just before lockup?
Also, you can hit the escape key when rebooting and use the recovery mode kernel.

In fact output the /boot/grub/menu.lst and /etc/fstab so we can maybe help.

The remastercd should have create an ISO somewhere, maybe tmp directory. It may be useless now since you in effect stopped it progress while it was making the ISO. Next time go have coffee and let it try to finish. So times we think its frozen but in fact it still progressing.

---

### Post by seanhvw on 2008-06-04
Yeah i think I may have panicked a bit. I left the laptop at home, but will try to check the output. But I think I am booting into the ISO I made judging from the Install icon I have on the desktop. Will poat more tonight.

Sean :)

---

### Post by bryanl on 2008-06-04
unless something has changed since I last installed it, remastersys should do nothing to your existing system. It just creates a bootable DVD structure in /home/remasterys, copies your system to that structure using squashfs to compress things, copies casper to get the Ubuntu live disk and install capability, then creates an iso from this structure. 

You need to make sure you have plenty of room in your home partition for the DVD images. Then you can create a bootable DVD with your system backup.

There is an /etc/remastersys.conf that has a list of directories to exclude in addition to those it already knows to avoid. The script uses rsync to do the copy. 

Note that remastersys is a system backup and should not be used for data. 'remastersys dist gets me an iso that is about 1 or 2 GB. If I am careful to remove most of the crud from my home directory, I can use 'remastersys backup' and get a disk image that will still fit on a standard DVD.

If the DVD image gets too large, you'll never know until you look for it and can't find it. mkisofs seems to max out at 4 GB or somewhere.

If you fill up the home partition, you are going to have some other problems to deal with depending upon how you have your system structured.

I run remastersys from the terminal with sudo. I took a look at the GUI and didn't see any advantage there.

---

### Post by seanhvw on 2008-06-04
VMC,
Here is a copy of my menu.list

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d99bb7bd-9736-40d6-a14c-6a0d48fefb0c ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d99bb7bd-9736-40d6-a14c-6a0d48fefb0c ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d99bb7bd-9736-40d6-a14c-6a0d48fefb0c ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d99bb7bd-9736-40d6-a14c-6a0d48fefb0c ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d99bb7bd-9736-40d6-a14c-6a0d48fefb0c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d99bb7bd-9736-40d6-a14c-6a0d48fefb0c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

And Fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d99bb7bd-9736-40d6-a14c-6a0d48fefb0c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=05007249-2043-48d9-a48a-5727d52cf935 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by VMC on 2008-06-04
One last bit of info will help: sudo fdisk -l

I see that you have Windows loaded. Does it work? Also have you tried to use a different kernel. I noticed that you have kept several ones.

---

### Post by seanhvw on 2008-06-05
The windows partition works, i just use it for games, until I get a better handle on WINE. The other partition (18) appeared after the Remastersys, but I have tried to load one of the others and they all appear to be wrong. I had modified my Kernel to run the mod for the touchpad and none of these have that. So I'm not sure what exactly happened. Going to try Disk Usage and see in there is an .iso sitting on my drive that I am trying to run from.

Sean :confused:

---

