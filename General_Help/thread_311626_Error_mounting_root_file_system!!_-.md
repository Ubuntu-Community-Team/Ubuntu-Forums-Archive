---
title: "Error mounting root file system!! -"
date: 2006-12-03
forum: General Help
---

### Post by minijai on 2006-12-03
Hello,
I've installed Ubuntu 6.06 LTS since September and all go right.

However two weeks ago when I started my computer fail.

I get the follow message:

Error mounting root file system and show me a black console (BusyBox) to write commands that don't respond.

I don't installed any software or hardware recently..

I use Ubuntu 6.06 LTS for AMD x64 - generic, using a MAXTOR SATA Hardrive, and my kernel version is 2.6.16-27.
I've proved to start with acpi=off parameter in the kernel but nothing happends!!!!!

If I boot with live-CD I can mount /dev/sda3 and I can access to any file, so the hard drive is OK!!!!

Any idea!!!



The output of fdisk -l is below, and menu.lst too.

```
---------------------------------------------------------------------
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       19253     1052257+  82  Linux swap / Solaris
/dev/sda3           19254       30005    86365440   83  Linux
/dev/sda4           30006       30515     4096575    b  W95 FAT32

--------------------------------------------------------------------------
``````
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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
updatedefaultentry=true

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
boot

#title          Ubuntu, kernel 2.6.15-26-amd64-generic
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-26-amd64-generic
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro single
#initrd         /boot/initrd.img-2.6.15-26-amd64-generic
#boot

#title          Ubuntu, kernel 2.6.15-25-amd64-generic
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/sda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-25-amd64-generic
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-25-amd64-generic (recovery mode)
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/sda3 ro single
#initrd         /boot/initrd.img-2.6.15-25-amd64-generic
#boot

#title          Ubuntu, kernel 2.6.15-23-amd64-generic
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-23-amd64-generic
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro single
#initrd         /boot/initrd.img-2.6.15-23-amd64-generic
#boot

title           Ubuntu, memtest86+
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
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
-------------------------------------------------------------------------
```

--------------------------------------------------------------------------
fstab
--------------------------------------------------------------------------
```
# /etc/fstab: static file system information.
#
#
proc /proc proc defaults 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda2 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda4 /media/puente vfat iocharset=utf8,umask=000 0 0
```

I can't run my ubuntu operating system since two weeks ago!!!
Thanks, I need Help!!!!! ](*,)

---

### Post by Joshua Hesketh on 2006-12-03
Have you tried a fsck (file system check) from the live CD?

---

### Post by minijai on 2006-12-03
I've tried that command and tell me that 
```
/dev/sda3: clean, ....
```

So, I think it's correct!!!

Any idea.](*,) ](*,)

---

### Post by Joshua Hesketh on 2006-12-04
hmm, I'm a little stumped sorry. My best idea would be to try the hard drive in another computer (boot off it) to see how it handles it. But I'm not sure where that will lead and if it would help. Sorry.

---

### Post by wgscott on 2006-12-05
It looks to be a known bug:

[https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/67130](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/67130)

I thought the CDs were free (they are to download) but this is one cockroach of a bug.  I would ask for my money back if I was you.

---

