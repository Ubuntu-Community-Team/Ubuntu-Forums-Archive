---
title: "Installing a second OS without the CD drive"
date: 2007-02-03
forum: General Help
---

### Post by ravemjr on 2007-02-03
Hey,

A couple of days ago my WinXP partition got infected, so I decided to reinstall everything.
The thing was my cd drive was dead: it can only read DVD's.
So I searched the net for tutorials on how to install it without one, and came across an interesting idea: create a FAT32 partition, copy the CD files there (specifically the /I386 folder) and boot using a DOS floppy.
All went fine, until the first install finished. Now I'm stuck with my Linux, which I didnt want to get rid of, the CD's FAT partition, and an extra FAT partition with 12mb's worth of windows files.
From what I've read in the last few days, the NT bootloader is in there, so that probably means it is accessible, but GRUB won't budge when I choose Windows XP.

Should I modify the menu.list? What should I put?

---

### Post by meng on 2007-02-03
What's in your menu.lst? Please show the output of:

cat /boot/grub/menu.lst


AND also

sudo fdisk -l
(that's L as in Larry)

---

### Post by ravemjr on 2007-02-03
Here's the menu.lst:
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
default		8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

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
# kopt=root=UUID=465559c7-cc66-4321-b232-222132daa9e1 ro

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=465559c7-cc66-4321-b232-222132daa9e1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=465559c7-cc66-4321-b232-222132daa9e1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=465559c7-cc66-4321-b232-222132daa9e1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=465559c7-cc66-4321-b232-222132daa9e1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=465559c7-cc66-4321-b232-222132daa9e1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=465559c7-cc66-4321-b232-222132daa9e1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

...and heres my Fdisk -l output:
```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2627    21101346    b  W95 FAT32
/dev/hda2            2628        3319     5558490   83  Linux
/dev/hda3            3518        3648     1052257+  82  Linux swap / Solaris
/dev/hda4            3320        3517     1590403+   c  W95 FAT32 (LBA)

Partition table entries are not in disk order

```

Sorry about the big menu.lst...haven't gotten around to cut the useless old kernel links...

---

### Post by meng on 2007-02-03
Looks fine to me, I can't explain why it doesn't work. I was curious to see your Windows partition is FAT32 rather than NTFS, though.

---

### Post by ravemjr on 2007-02-03
I wasn't aware of that myself, but I also found a post saying you could...then convert it after you installed it if you wanted to.

Anyway, here's the contents of the partition:
```
bootfont.bin  boot.ini  bootsect.dos  inf000.swp  inf001.swp  $ldr$  ntdetect.com  ntldr  txtsetup.sif  $win_nt$.~bt  $win_nt$.~ls

```

I guess that's install files that you get on the disk after the first boot...after that the disc boots, and continues the install from there, since DOS installing is TOO slow, even with smartdrive.
Does it have with anything to do with the fact that it was on NTSC when i installed GRUB and now it's changed to FAT?

---

