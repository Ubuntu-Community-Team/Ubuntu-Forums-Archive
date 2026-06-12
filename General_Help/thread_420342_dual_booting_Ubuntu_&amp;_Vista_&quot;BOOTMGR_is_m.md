---
title: "dual booting Ubuntu &amp; Vista &quot;BOOTMGR is missing&quot;"
date: 2007-04-23
forum: General Help
---

### Post by VinceDee on 2007-04-23
UPDATE: I booted into Vista using the Vista dvd, selected the "repair windows" option, and had it replace the bootmanager. Oddly, it didn't erase grub when it did this, so when I rebooted grub came up, I hit "esc" and picked Vista and it booted up just fine. My Ubuntu installation still works fine, too.

ORIGINAL MESSAGE
I've already searched and tried a number of listed fixes, but no luck. I'm still getting the "BOOTMGR is missing" when I select Vista from my grub boot menu.

I have one hard drive (hd0) divided into two partitions (0 and 1). I installed Vista on the second partition (as has been suggested for dual booting), then I installed Ubuntu (Feisty) on the first partition.

Then I modified the /boot/grub/menu.lst and added:

title             Windows Vista
root             (hd0,1)  #my only hard drive, the second partition
makeactive
chainloader +1

I've also used **rootnoverify** and **savedefault** at various times, and tried other combinations of partitions such as **(hd0,0)** **(hd0,2) **etc. But I'm positive that my Windows partition is at hd0,1 because I ran:

```
grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   **Partition num: 1,  Filesystem type unknown, partition type 0x7**
   Partition num: 4,  Filesystem type unknown, partition type 0x82
```

Anyone have solutions or ideas?

Vince


EDIT: 
Here's my fdisk -l
```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       11708    94044478+  83  Linux
/dev/hda2   *       12211       24322    97278976    7  HPFS/NTFS
/dev/hda3           11709       12210     4032315    5  Extended
/dev/hda5           11709       12210     4032283+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

EDIT #2
Here's my menu.lst
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
timeout		5

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
# kopt=root=UUID=4b37da36-23a2-4a60-a16b-dd746316df17 ro

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

## ## End Default Options ##

title		Windows Vista
rootnoverify	(hd0,1)
makeactive
chainloader +1

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4b37da36-23a2-4a60-a16b-dd746316df17 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4b37da36-23a2-4a60-a16b-dd746316df17 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by redwdc on 2007-04-23
One thing to do is you need to put your vista entry either at the top like this:

```

#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		Windows Vista
rootnoverify	(hd0,1)
makeactive
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST

```

or at the bottom like this:

```

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows Vista
rootnoverify	(hd0,1)
makeactive
chainloader +1

```

If you put it the top it will be first on the list.  Or you can set to be the default boot by following these instructions from the grub "menu.lst"

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

```
red

---

### Post by VinceDee on 2007-04-23
Thanks for the reply. 

I tried both of your suggestions and it still didn't work...same result each time (BOOTMGR is missing).

Anything else?

Vince

---

