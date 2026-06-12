---
title: "Dual Booting Problems"
date: 2008-07-04
forum: General Help
---

### Post by mrblue182 on 2008-07-04
You are probably going to laugh at my stupidity for doing this, but I have 2 harddrives, one that came w/ my computer (only 80 gigs, so i didn't want to partition it) with windows that I use for video games. And another with ubuntu on it. This is where it probably went wrong. In order to change between the harddrives, I would go into BIOS and enable/disable the ubuntu harddrive. Now, my windows is corrupt. If there is any way to recover without reformatting, it would be greatly appreciated.

---

### Post by VMC on 2008-07-04
> **mrblue182 said:**
> You are probably going to laugh at my stupidity for doing this, but I have 2 harddrives, one that came w/ my computer (only 80 gigs, so i didn't want to partition it) with windows that I use for video games. And another with ubuntu on it. This is where it probably went wrong. In order to change between the harddrives, I would go into BIOS and enable/disable the ubuntu harddrive. Now, my windows is corrupt. If there is any way to recover without reformatting, it would be greatly appreciated.

So you used the BIOS to switch between Windows and ubuntu? I'm unclear how you did that, but set the BIOS back to normal setting using both drives.

You hve a few options to use. Changing the MBR won't effect Windows. So boot up ubunto and type two things:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

As far as recover Windows. Do you have a recover disk? Also what version of Windows, and what error messages.

---

### Post by mrblue182 on 2008-07-05
I would turn on and off my ubuntu harddrive that was in slot one to change. I am using windows XP, and I only changed 1 setting that I set back to normal.

I have two different harddrives, and can't access the windows one via ubuntu anymore either.

And yes, I do have a backup CD, but I would prefer to keep all of my files and programs.

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046af4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29834   239641573+  83  Linux
/dev/sdb2           29835       30401     4554427+   5  Extended
/dev/sdb5           29835       30401     4554396   82  Linux swap / Solaris

```

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=8995606c-4589-44ae-8357-591b42be8972 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8995606c-4589-44ae-8357-591b42be8972 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8995606c-4589-44ae-8357-591b42be8972 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8995606c-4589-44ae-8357-591b42be8972 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8995606c-4589-44ae-8357-591b42be8972 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8995606c-4589-44ae-8357-591b42be8972 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8995606c-4589-44ae-8357-591b42be8972 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by VMC on 2008-07-05
Okay your setup is typical. You can see that the grub menu doesn't show Windows. But you need to get Windows fixed before you continue. 

Put in your Windows recovery disk and see if you can fix it that way. What exactly do you mean by correct. What Windows message comes out. Maybe 'fixmbr'.

---

### Post by mrblue182 on 2008-07-09
I had to reformat my harddrive, but all is well now.

Oh, and thanks to your signature, I found out how to dual boot using grub =]

---

### Post by Cap'n Skyler on 2008-07-09
for emergency use....you may want to keep one super grub disk around :)
[http://http://supergrub.forjamari.linex.org/?section=home]("http://http://supergrub.forjamari.linex.org/?section=home")

---

