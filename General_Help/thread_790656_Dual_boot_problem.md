---
title: "Dual boot problem"
date: 2008-05-11
forum: General Help
---

### Post by Joe of loath on 2008-05-11
hi;

well, hardy is now working great. (except from that damn radeon 9600 driver! not a problem unless i play games though.)

the only problem is, i need windows to play games and for my computer illiterate sister to use. i followed a few dual boot guides, but nothing works. first, when i pressed the button in grub to load windows the screen just flashed and nothing happened. now, i get grub error 13. none of the fixes online seem to work.

here's my menu.lst file:

joe@henry-linux:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=0e9438e6-335c-40a8-af42-ca22ea462c64 ro

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
# defoptions=quiet splash acpi=off

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0e9438e6-335c-40a8-af42-ca22ea462c64 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0e9438e6-335c-40a8-af42-ca22ea462c64 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Home
rootnoverify		(hd0,1)
makeactive	
chainloader	(hd0,1)+1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


as you can see, windows is installed on the second active partition (theres a swap partition in the middle, but thats extended so doesn't count)

thanks for any help;
Joe

---

### Post by meierfra. on 2008-05-11
> theres a swap partition in the middle, but thats extended so doesn't count)

It does count. Please post the output of

```
sudo fdisk -l
```
( l is a lower case L)

---

### Post by Joe of loath on 2008-05-12
ok theres something VERY strange here;

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9726    78124063+  83  Linux
/dev/sda2   *        9727       10297     4586557+  82  Linux swap / Solaris
/dev/sda3           10298       20023    78124095    7  HPFS/NTFS

the swap partition is labelled as boot? how can this be?

EDIT: i must have made a mistake, i set the first partition as boot and i'm going to see if that works...

oh, and should it be:

title Windows XP Home
Root (hd0,2)
makeactive
chainloader +1

instead?

sorry, i know my way around the shell, but grub is new to me, and i'm clueless.

thanks
Joe

---

### Post by Joe of loath on 2008-05-12
ok, after the reboot it's set the swap partition as boot again. WTF?

---

### Post by meierfra. on 2008-05-12
the "makeactive" statement in the menu.lst sets the boot flag to the root device. So

root (hd0,1)
makeactive

sets the boot flag to (hd0,1). And since (hd0,1) is you swap partition, the boot flag is set to the the swap  partition every time your reboot.


The correct Windows  entry should be

title Windows XP Home
root (hd0,2)
makeactive
chainloader +1

(it need to be "root" and not "Root")

This will automatically set the boot flag to the Windows partition (and that's where it should be)

---

### Post by Joe of loath on 2008-05-12
thanks, i came to the same conclusion eventually. i'm now posting from a horrible blue window in horrible blue windows downloading the inevitable drivers...

it must have been gremlins.

---

