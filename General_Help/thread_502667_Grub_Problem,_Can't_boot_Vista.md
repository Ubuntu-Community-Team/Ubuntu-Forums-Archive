---
title: "Grub Problem, Can't boot Vista"
date: 2007-07-16
forum: General Help
---

### Post by DuneSoldier on 2007-07-16
Hi, I have a problem. I just installed Ubuntu 7.04 to my secondary hard-drive. I have Vista installed on the primary hard-drive. I can boot in to Ubuntu fine, but I can't boot in to Vista. Grub hangs with "starting up ..." displayed on the screen. I'm not sure what's wrong, I checked my /boot/grub/menu.lst, and that looks ok to me. I also used my Vista install CD and used the BCDEdit program, and that looks fine to me as well.

My Menu.lst file:

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
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=35e862af-5730-44bc-9bf2-89c196fbda54 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=35e862af-5730-44bc-9bf2-89c196fbda54 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=35e862af-5730-44bc-9bf2-89c196fbda54 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista
root            (hd0,0)
makeactive
chainloader     +1

My Device Map file:

(hd0)   /dev/sda
(hd1)   /dev/sdb

And lastly the output of sudo fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

I really appreciate any help, thanks.

---

### Post by DuneSoldier on 2007-07-16
Oh, if it matters I'm using the 64 bit edition of Vista Home Premium and the 64 bit edition of Ubuntu.

---

### Post by confused57 on 2007-07-16
Your menu.lst looks OK, based on your fdisk -l...Have you tried restoring your Vista IPL to the mbr, using your Vista install DVD?  It's just a suggestion and if your bios is able to boot first to your Ubuntu drive, if it were my system, I would use the live cd to install grub to the Ubuntu drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
e.g.
```
root (hd1,0)
setup (hd1)
```

Then if you boot first to your Ubuntu drive and get a grub boot menu, highlight your Ubuntu entry, press "e" to edit, highlight the root line, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot...this change is temporary, but can be made permanent if it works and you want to have your system set up this way.

You might be able to boot Vista from the grub boot menu installed to the Ubuntu drive's mbr...

---

### Post by DuneSoldier on 2007-07-16
Thanks for your reply. I don't know how to restore the vista IPL to my boot loader. I remember being able to do an fdisk /fixmbr back when I had a floppy drive. The Vista recovery disk doesn't have fdisk on it.

---

### Post by confused57 on 2007-07-16
> **DuneSoldier said:**
> Thanks for your reply. I don't know how to restore the vista IPL to my boot loader. I remember being able to do an fdisk /fixmbr back when I had a floppy drive. The Vista recovery disk doesn't have fdisk on it.
You would probably need a Vista install DVD to restore the mbr, don't think you can do it with a recovery disk...

I don't know if you might be able to boot your Vista with the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by DuneSoldier on 2007-07-16
Well I have a Vista Install Disc. I bought one retail since it had just come out when I built this PC. I'm looking through the Super Grub page now. Thanks.

---

### Post by confused57 on 2007-07-17
> **DuneSoldier said:**
> Well I have a Vista Install Disc. I bought one retail since it had just come out when I built this PC. I'm looking through the Super Grub page now. Thanks.

I don't have Vista, but I think you can boot up the install DVD and select something like "Startup Repair".

---

### Post by DuneSoldier on 2007-07-17
> **confused57 said:**
> I don't have Vista, but I think you can boot up the install DVD and select something like "Startup Repair".

I've done that, Vista claims it detects no problems with startup.

---

### Post by DuneSoldier on 2007-07-17
Awesome, I found out how to fix the MBR in the Vista Recover Disk. Open a recovery console and type the command 'bootrec /mbr'. I can get back in to Vista now, thanks for all your help. I'm going to wait and tackle getting Grub working this weekend, as you suggested I can change the boot order of my hard-drives and install grub on the one where Linux is.

Thanks again.

---

### Post by confused57 on 2007-07-17
You might try rootnoverify, instead of root:
```
title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1
```

If this doesn't work hopefully SGD will be able to boot Vista.

---

### Post by confused57 on 2007-07-17
> **DuneSoldier said:**
> Awesome, I found out how to fix the MBR in the Vista Recover Disk. Open a recovery console and type the command 'bootrec /mbr'. I can get back in to Vista now, thanks for all your help. I'm going to wait and tackle getting Grub working this weekend, as you suggested I can change the boot order of my hard-drives and install grub on the one where Linux is.

Thanks again.
Great, just checked back in and saw you were able to get Vista's IPL reinstalled...I'll have to make a note of how you did this, for future reference, thanks for the update.

You shouldn't have any problems getting grub installed to your Ubuntu drive's mbr & boot to the Ubuntu drive first.

---

