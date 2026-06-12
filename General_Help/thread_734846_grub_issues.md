---
title: "grub issues"
date: 2008-03-25
forum: General Help
---

### Post by [z]er0 HP on 2008-03-25
Hi i am having some confusion with howto reconfigure grub for my new configuration.
I have 2 x 500gb hard drives and 1 x 120gb hard drive.

sda is the first 500gb hard drive, it has a windows xp partition and a full ntfs partition. I would like to leave it as is.

sdb has an ubuntu installation on it and i would like to add the entry to grub (its the main issue)

sdc is my current ubuntu installation which is soon to be formatted and have windows xp on it.

Could someone please:
show me the modifications needed to add my second ubuntu installation into the grub boot menu.
show me the modifications needed to add my soon to be installed of windows xp installation into the grub boot menu.
Show me a tutorial or explain to me how the linux addressing system (sdx) relates to windows (x:\) 

[QUOTE="sudo fdisk -l"]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe454e454

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000db36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59572   478512058+  83  Linux
/dev/sdb2           59573       60801     9871942+   5  Extended
/dev/sdb5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b559b55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803435    5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris
[/quote]



[quote="sudo cat /boot/grub/menu.lst"]
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)


# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b60d1b1d-9d94-45c6-9d27-a71ae7e3db11 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b60d1b1d-9d94-45c6-9d27-a71ae7e3db11 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b60d1b1d-9d94-45c6-9d27-a71ae7e3db11 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1
[/quote]

---

### Post by LaRoza on 2008-03-25
You will need to reinstall grub anyway when you install Windows.

Grub is on the current install (sbc), and when you install Windows Grub will be gone.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

> 
Show me a tutorial or explain to me how the linux addressing system (sdx) relates to windows (x:\)


Windows uses drive letters for devices because an ancient operating system called CP/M used it (C: was for CP/M, see?) and MS-DOS had to be compatible with it to be used. It has retained this ancient scheme and is quite limited by it.

In *nix systems, everything is a file. Your printer is a file, your webcam is a file, and disks are files. They are all under root (/), and to "mount" something it just adds it to the tree.

Devices are under /dev/, and the mountpoints are usually in /media/ unless otherwise specified. In the new kernels, disks are named "sdx". If you have SATA drives:

```

/dev/sda == First sata drive (on controller 0)
/dev/sdb == Second sata drive (on controller 1)
/dev/sdc == You get the picture...

```

On each drive, there is a number which shows the partition.

```

/dev/sda0 == First primary partition of /dev/sda
/dev/sdb1 == Second primary partition of /dev/sdb
...and so on.

```

(Remember that it starts at 0, logically)

In Windows, Window is installed to C:, which can be anywhere. So it is impossible to give a guide to "translating" the schemes here.

---

