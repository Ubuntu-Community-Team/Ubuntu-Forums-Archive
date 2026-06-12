---
title: "GRUB after changing Win 2000 to XP"
date: 2008-02-25
forum: General Help
---

### Post by themad on 2008-02-25
I had Windows 2000 and Mint Linux, and I changed Windows 2000 on XP. To get GRUB back, I fixed GRUB with Mint Live CD and GRUB worked, Mint is booting succesfully, but when I try to boot Windows XP, there is an error. I can't boot it. I also tried to restore GRUB by Super Grub Disk, but there is the same error.
When I restore Windows's MBR by Super Grub Disk, Windows is booting normaly (but there isn't GRUB loading).

How could I do (without re-installing Mint) to make GRUB with Windows XP?

sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5aae5aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2432    19527007+   f  W95 Ext'd (LBA)
/dev/sda2            2433        2681     2000092+  82  Linux swap / Solaris
/dev/sda3            2682        5171    20000925   83  Linux
/dev/sda4   *        5172        9729    36612135    b  W95 FAT32
/dev/sda5               2        2432    19526976    b  W95 FAT32

```

cat /boot/grub/menu.lst
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default         0

gfxmenu=/etc/grub/message.mint

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title           Linux Mint, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by ghost_ryder35 on 2008-02-25
i think your best bet is to use the Super Grub CD to "fixboot" and "fixmbr" on Windows.  That will successfuly recover your windows but will kill most likley your Grub boot loader.  Then you can use the Super Grub CD again or the Mint cd and reinstall grub, it should then auto detect just like it did when it was first installed.

---

### Post by themad on 2008-02-25
I did what you say, but GRUB is fixing, not reinstalling - the title of Windows is still the same.

The grub error code is 12:

12 : Invalid device requested.

---

