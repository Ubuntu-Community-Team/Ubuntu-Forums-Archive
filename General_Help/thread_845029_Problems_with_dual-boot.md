---
title: "Problems with dual-boot"
date: 2008-06-30
forum: General Help
---

### Post by emavio on 2008-06-30
I have an Ubuntu/WinXP dual-boot machine. The GRUB bootloader menu allowed me to boot into several Ubuntu options or into WinXP.
After an unattended-upgrade my file /boot/grub/menu.lst was modified.
Although   the following lines look OK:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

when I choose  the Windows XP OS option the following error message is displayed:
**unrecognized device string**

Please suggest me the cause of this behaviour!

---

### Post by ajmorris on 2008-06-30
hi there,
can you post the output of sudo fdisk -l from a terminal please.

AJ

---

### Post by emavio on 2008-06-30
Here you can see what is displayed after the command sudo fdisk -l:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7114    57143173+   7  HPFS/NTFS
/dev/hda2            7236        9729    20033055   83  Linux
/dev/hda3            7115        7235      971932+  82  Linux swap / Solaris

Partition table entries are not in disk order

Thanks!

---

### Post by WRDN on 2008-06-30
Can you post the entire contents of your menu.lst file please.
Also, please use the [CODE] tags around it to make it easier to read.
Thanks

---

### Post by emavio on 2008-06-30
Here is mu menu.lst  file:


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
# kopt=root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro

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
# defoptions=nosplash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro nosplash
initrd		/boot/initrd.img-2.6.20-17-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro nosplash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro nosplash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro nosplash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro nosplash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=f5fa72f9-afb1-48a7-81fb-6b67df9ffe15 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
 
```

---

### Post by enchesss on 2008-06-30
are you using 1 hard drive with dual boot

if so try changing the last line:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows 95/98/Me
root		(hd1,0)
```

so change this:

```
root		(hd1,0)
```

to this:

```
root		(hd0,0)
```

---

### Post by emavio on 2008-06-30
@enchesss  I have two hard drives, and I didn't try to select
Windows 98. In this case is the pointed change good?
Thanks!
ema

---

### Post by enchesss on 2008-06-30
it looks to me like the output of

```
sudo fdisk -l
```

is only showing one hard drive


```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 7114 57143173+ 7 HPFS/NTFS
/dev/hda2 7236 9729 20033055 83 Linux
/dev/hda3 7115 7235 971932+ 82 Linux swap / Solaris

Partition table entries are not in disk order
```

this one is too hard for me

your mbr and boot mapping is different to the basic setup and this is probably why grub has been altered incorrectly with the update. Have never seen the map lines before.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

these lines have been added 

```
map		(hd0) (hd1)
map		(hd1) (hd0)
```

and this may be confusing the grub installation.

do you really need two versions of windows?

Are you trying to put linux on a partition of one of these drives?

---

### Post by danwood76 on 2008-06-30
The map command is to allow booting windows off a secondary drive.
(Windows hates being no. 2 in a system)

Your grub setup looks fine, if it boots ubuntu fine then it should boot windows equally fine.
Are you sure you havent done anything nasty to windows?

Also what is the exact error code grub throws out when you select XP?

---

### Post by emavio on 2008-06-30
@danwood76 when I select other OS (before Windows XP was listed explicitely
as an option, but now appears only other OS!) it is displayed the error message:
**unrecognized device string**

ema

---

### Post by danwood76 on 2008-06-30
Im assuming you are selecting the wrong entry in the grub menu, I bet the line says this:
```

Other operating systems:

```
This is just a divider and wont do anything, if you hit down you should see 'Windows XP Professional'

This can be seen in the last section of your menu.lst:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
Notice the other OS section and below it the XP section, make sure you select XP.

---

### Post by emavio on 2008-06-30
@danwood76

I did not refer to menu.lst but to what is listed when booting.
I saw the Windows XP option in menu.lst but it does not appear on the 
screen when I restart the computer. There are displayed many Ubuntu options and finally other OS. When I choose other OS the above error message is shown.

ema

---

### Post by danwood76 on 2008-06-30
Are you sure you have scrolled to the bottom of the list?

It might be that because there are quite a few entries the bottom ones arent displayed except if you scroll down to them.

The Other OS option will not boot an OS as it has no device entries or boot options so it gives you that error.

---

### Post by emavio on 2008-06-30
> **danwood76 said:**
> Are you sure you have scrolled to the bottom of the list?

It might be that because there are quite a few entries the bottom ones arent displayed except if you scroll down to them.

The Other OS option will not boot an OS as it has no device entries or boot options so it gives you that error.

Yes, you are right! Thank you very much!

ema

---

