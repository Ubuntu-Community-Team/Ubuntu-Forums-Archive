---
title: "Grub Error 21 - but okay after reboot?"
date: 2006-12-28
forum: General Help
---

### Post by jbrams on 2006-12-28
I recently installed 6.10 on slave hdd, prior installation of Windows XP SP2 on ntfs primary drive (hdc1).  When powering on, after bios loading screen, grub reports the following:

Grub loading state1.5
Grub error 21

But when I restart (using restart button on PC tower) everything works just as it should and I'm presented with a list of OS's to boot (ubuntu, WinXP).  That's okay for now, but what is the cause of the error after "cold" starting the computer (from a power off rather than a restart) and how can I correct it?

Here's my (1) Fstab and (2) menu.lst

Fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=509e5ac6-ff56-44db-8672-20beaf4f6134 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=31fe7c0c-05a0-4876-89f5-2e688b1b5131 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd3 /home ext3 nodev,nosuid 0 2
/dev/hdc1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=509e5ac6-ff56-44db-8672-20beaf4f6134 ro
# kopt_2_6=root=/dev/hdd1 ro

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

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by dcstar on 2006-12-28
> **jbrams said:**
> I recently installed 6.10 on slave hdd, prior installation of Windows XP SP2 on ntfs primary drive (hdc1).  When powering on, after bios loading screen, grub reports the following:

Grub loading state1.5
Grub error 21

But when I restart (using restart button on PC tower) everything works just as it should and I'm presented with a list of OS's to boot (ubuntu, WinXP).  That's okay for now, but what is the cause of the error after "cold" starting the computer (from a power off rather than a restart) and how can I correct it?
.......

Possibly Grub is trying to load before your hard disk(s) are ready, is there a setting in your BIOS to add in a boot delay to allow things to settle down?

---

### Post by jbrams on 2006-12-28
> Possibly Grub is trying to load before your hard disk(s) are ready, is there a setting in your BIOS to add in a boot delay to allow things to settle down?
I'll reboot right now and check it out, thanks for the fast reply!

---

### Post by jbrams on 2006-12-28
Well, it didn't repeat the error after a few shutdown - startup attempts.  I changed a few settings in BIOS including disabling "quick boot" which isn't what you described but may have the same effect that you discussed above (enough delay for the disk with ubuntu to startup).

---

