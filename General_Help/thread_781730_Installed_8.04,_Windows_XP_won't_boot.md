---
title: "Installed 8.04, Windows XP won't boot"
date: 2008-05-04
forum: General Help
---

### Post by DrFugly on 2008-05-04
Hello all! Thanks for reading this and helping me out!

Setup: I have 2 hard drives, a 40gig and a 120 gig. The 120gig has my Windows XP installation. I can mount it and can look into it. The data is still there, fully modifyable and I've used wine to run some programs on it. Everything looks ok in there.
The 40 gig hard drive is what I've installed Ubuntu on, and am currently writing this post to you with.

I installed hardy heron on this drive yesterday with no problem, but now today I tried to boot windows. When i try to boot windows the loading bar on the bottom (Not colorful windows xp boot screen, the black screen with a white bar across the bottom) fills up but then freezes. I restart the machine, try to load windows again, It says that there was a problem booting, select: boot normally, boot into safe mode, boot into command prompt, etc... No matter which of these options i pick the same thing happens.

Here is my fdisk -l output:

```
Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca35ca35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14595   117234306    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70087008

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris
```

and here is my /boot/grub/menu.lst file
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
# kopt=root=UUID=1e8e9b15-2fa5-408e-ba50-637c30423ac5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1e8e9b15-2fa5-408e-ba50-637c30423ac5 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1e8e9b15-2fa5-408e-ba50-637c30423ac5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root	(hd0,0)
savedefault
makeactive
chainloader	+1

```

Thank alot every one! Does any one know what the problem is?

---

### Post by DrFugly on 2008-05-04
I hate to double post, but this is really bugging me, searching online most articles just deal with getting to the grub menu, I can get to the menu, I can't get XP to boot!

Edit: Got everything back up and running again on my own.
Some how through installing hardy heron something happened to my windows installation (even though that hard drive shouldn't have been touched) and grub was written onto my 120GB windows hard drive... which killed my XP installation.

The process of fixing this:

1.) Get my hand on the windows XP cd, boot to it, run a recovery installation (I tried bootcfg and fixmbr, neither worked, just made matters worse)
2.) You'll notice that grub doesn't pop up any more, good, Windows XP overwrote the whole boot up process. So the next step it to use that ubuntu live cd and boot to it. (Don't use the ubuntu on the harddrive, boot straight off the CD) and reinstall grub (There are plenty of resources on that online). Then make sure that your menu.lst file is ok to go (I had a panic attack when none of my grub options worked after the reinstall... found out that it got my menu.lst file wrong)
3.) Enjoy!

---

### Post by thezood on 2008-05-11
I have the same problem. The only difference is that my machine reboots a couple of seconds into the Windows boot procedure. I'd really like to repair this without having to delete all the Windows program settings. Does recovery installation of Windows keep the program settings?


Regards,
anders.

---

