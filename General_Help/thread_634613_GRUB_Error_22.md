---
title: "GRUB Error 22"
date: 2007-12-07
forum: General Help
---

### Post by halflife28 on 2007-12-07
I believe I have all my settings right, but somehow GRUB doesn't want to play nice and throws error 22 saying the partition isn't there, when it is, and the root command is pointing to the right location. It's as if it cannot read from the partition itself.

I have 3 hard drives, ignore the first 2 and focus on sdc.

Heres fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fba1fb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78156193+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7a2e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9730    78148632   42  SFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x551df432

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8687    69769531+   7  HPFS/NTFS
/dev/sdc2            8688        9678     7960207+  83  Linux
/dev/sdc3            9679        9729      409657+   5  Extended
/dev/sdc5            9679        9729      409626   82  Linux swap / Solaris

```

And heres menu.lst:
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
# kopt=root=UUID=2f84a031-e866-464a-b85a-a150505296a5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f84a031-e866-464a-b85a-a150505296a5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f84a031-e866-464a-b85a-a150505296a5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista Ultimate
root		(hd2,0)
savedefault
chainloader	+1

```

---

### Post by logos34 on 2007-12-07
On the grub menu screen hit 'e' to edit the ubuntu entry, and 'e' again on the 'kernel' line...try (hd**1**,1) of (hd**0**,1).  Then 'b' to boot.  Maybe the drives are being seen by grub in a different order now...If one of the above works and you can boot into ubuntu, make the change permanent by changing menu.lst

---

### Post by teryowen on 2007-12-07
hmm everything seems like it should work... does your computer even load up GRUB?

---

### Post by rsambuca on 2007-12-07
> **teryowen said:**
> hmm everything seems like it should work... does your computer even load up GRUB?

Well of course it is.  Grub Error 22!!!  It is a stage 2 error.  It can't find the partition with the menu.list.

---

### Post by teryowen on 2007-12-07
I thought that if it doesn't load up the menu.lst its technically not considered loaded.

So he should probably do this:

Boot of a live CD and in terminal type the following in:

```

sudo grub
root (hd2,1)
setup (hd2)
quit
```

this should fix it, let me know.

---

### Post by PmDematagoda on 2007-12-07
But it seems that the menu.lst file is correctly configured, but anyway, post the result of:-

```
cat /boot/grub/device.map
```

---

### Post by rsambuca on 2007-12-07
> **teryowen said:**
> I thought that if it doesn't load up the menu.lst its technically not considered loaded.

So he should probably do this:

Boot of a live CD and in terminal type the following in:

```

sudo grub
root (hd2,1)
setup (hd2)
quit
```

this should fix it, let me know.

The root is already set as (hd2,1).  It is the groot line.  This is not the problem.  The problem is that grub is guessing the drive order incorrectly.

---

### Post by PmDematagoda on 2007-12-07
> The root is already set as (hd2,1). It is the groot line. This is not the problem. The problem is that grub is guessing the drive order incorrectly.

That could be attributed due to incorrect entries in the device.map file.

---

### Post by rsambuca on 2007-12-07
> **PmDematagoda said:**
> That could be attributed due to incorrect entries in the device.map file.

I know, that is why I didn't say anything further.  I try not to complicate threads by giving repeat information.

---

### Post by PmDematagoda on 2007-12-07
Yes indeed rsambuca, but sometimes it is necessary to repeat the same thing in a different way so that it would be more accurate.

---

### Post by rsambuca on 2007-12-07
> **PmDematagoda said:**
> Yes indeed rsambuca, but sometimes it is necessary to repeat the same thing in a different way so that it would be more accurate.

I disagree, but fine, I'm outta here.

---

### Post by PmDematagoda on 2007-12-07
No, no, don't go on my part, if that is how you feel, then all right, I won't be doing that anymore, does that satisfy you?

I do not wish to create any antagonism since we are supposed to help people, so let's just forget about this and go on, shall we?

---

### Post by halflife28 on 2007-12-08
I loaded up the Windows Vista DVD and clicked Repair Computer and it said it fixed startup issues, and finally I could boot back up into Ubuntu and Windows Vista. Weird....

---

