---
title: "Grub error 15"
date: 2008-05-19
forum: General Help
---

### Post by BlueScotch on 2008-05-19
Okay, So I have one partition as follows:

/dev/hda1 ntfs -windows
/dev/hda4 ext3-unused--recently formatted
/dev/hda2 ext3-ubuntu 7.10
/dev/hda3 linux-swap

That information is what Gparted reports.  I originally had another version of ubuntu on hda4, but I formatted that (which I believe had the grub menu.lst file that was being used).  Now when I boot up all I get is Grub error 15.  I have gotten to the point where I boot up using a live cd and mounted hda2 (the linux partition which has an old grub file).

I am not sure what to do in order to point the grub installed on my system to point to hda2, which should have the correct boot information (I installed hda2 before hda4).

Any help would be greatly appreciated.


Thanks

---

### Post by TeoBigusGeekus on 2008-05-19
Boot up with the live cd and find the menu.lst file - post us its contents, if any. It should be located in the /boot/grub folder.

Post us as well the output of 
```
sudo fdisk -l
```
(-L)

---

### Post by BlueScotch on 2008-05-19
The results of fdisk -l is:


```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8357    67127571    7  HPFS/NTFS
/dev/hda2            9123       11565    19623397+  83  Linux
/dev/hda3           11566       12161     4787370   82  Linux swap / Solaris
/dev/hda4            8358        9122     6144862+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 126 MB, 126353408 bytes
16 heads, 32 sectors/track, 482 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         481      123120    b  W95 FAT32

```

---

### Post by TeoBigusGeekus on 2008-05-19
What about the menu.lst file?

---

### Post by housam on 2008-05-19
[[COLOR="Red"]_Reinstall grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3")

---

### Post by BlueScotch on 2008-05-19
the menu.lst from the only linux installation on my harddrive is on hda2 and is:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0cfb46c1-e61e-4eb6-99e1-d23ad033e973 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0cfb46c1-e61e-4eb6-99e1-d23ad033e973 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0cfb46c1-e61e-4eb6-99e1-d23ad033e973 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=0cfb46c1-e61e-4eb6-99e1-d23ad033e973 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=0cfb46c1-e61e-4eb6-99e1-d23ad033e973 ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



```

Sorry its long, I wasn't sure if I needed to post the entire thing or just the one section.

Thanks

---

### Post by TeoBigusGeekus on 2008-05-19
Unfortunately (!) your menu.lst has the correct information... Which means that it is not a problem of its contents, but of it having been removed by your late Ubuntu installation...
You're gonna have to restore grub. Follow housam's link and you should be ok...

---

### Post by BlueScotch on 2008-05-19
I have tried that article/information and I alter the commands to refer to hda2 (which is the grub that I want to use).  Everything goes fine until i have to run

```
chroot /mnt/work/ /bin/bash 
```

I get the error:

chroot: cannot run command '/bin/bash': Ecec format error.  Any idea where I should go from there?

---

### Post by BlueScotch on 2008-05-19
I have tried that article/information and I alter the commands to refer to hda2 (which is the grub that I want to use).  Everything goes fine until i have to run

```
chroot /mnt/work/ /bin/bash 
```

I get the error:

chroot: cannot run command '/bin/bash': Ecec format error.  Any idea where I should go from there?

---

### Post by louieb on 2008-05-19
Restoring Grub can be done from a live CD.
Just need to get to a grub shell.  
Heres one of the better how tos I have found.
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by BlueScotch on 2008-05-19
> **louieb said:**
> Restoring Grub can be done from a live CD.
Just need to get to a grub shell.  
Heres one of the better how tos I have found.
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

This worked for me.  Thanks so much, It was actually much easier then what I was trying.

---

