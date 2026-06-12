---
title: "grub error 17, can only boot edgy using &quot;Super Grub Disc&quot;"
date: 2006-11-22
forum: General Help
---

### Post by WBC on 2006-11-22
I was using Windows XP Pro and Ubuntu 6.10 dual booted with no problems for about 2 weeks and all of a sudden I could no longer boot to Ubuntu 6.10.  The Grub Bootloader gives me error 17.  I tried to reinstall the Grub bootloader via the command line but I still get error 17.

I looked on the internet and found a boot CD called "Super Grub Disc" and it will boot Ubuntu 6.10 using the "Boot Linux Directly" selection.  I tried the repair Grub bootloader function and the program reported "repaired successfully".  The problem still remains, it still would not boot using the standard grub bootloader?

How can I find the problem that is causing the error 17 and make Ubuntu boot again from the bootloader?  NOTE: Windows XP still boots fine from this same bootloader.](*,) :-k

---

### Post by Jason_25 on 2006-11-22
What steps did you use to recover grub from the command line?

Post #5 on [this]("http://www.ubuntuforums.org/showthread.php?t=24113") thread explains the way that always works for me.  Chances are you have a bad drive if that method doesn't work for you.

---

### Post by WBC on 2006-11-22
I first found what the drives being used are and then the menu.lst file.
sudo grub
find /boot/grub/stage1
quit
---------------------------------

grub> find /boot/grub/stage1


grub> 
-----

 Output= (hd0,6)

---------------------------------------------------

bill@bill-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/hda2            7834       30515   182193165    f  W95 Ext'd (LBA)
/dev/hda5            7834       20786   104044941    7  HPFS/NTFS
/dev/hda6           20787       23290    20113348+   7  HPFS/NTFS
/dev/hda7   *       23291       25692    19294033+  83  Linux
/dev/hda8           25693       25798      851413+  82  Linux swap / Solaris
/dev/hda9           25799       30515    37889271    7  HPFS/NTFS
bill@bill-ubuntu:~$ 

-------------------------------------------------------
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
default		5

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
# kopt=root=UUID=26d6dca7-3a3c-4825-9974-fc3d9f8726b0 ro
# kopt_2_6=root=/dev/hda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet
boot

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



-------------------------------------------------------

I used the "Super Grub Disc" CD to boot to Linux and used the terminal.


sudo grub
root (hd0,7)
setup (hd0)
quit


---------------------

I still get Grub error 17 which is said to be that grub can not reccognize the file system type?
I do not get it?  What's wrong?

WBC

---

### Post by geek_Man on 2006-11-27
Your Linux partition is on hda7. To GRUB that's hd0,6 because GRUB starts indexing at zero. So what you need to do is change the entries in menu.lst to (hd0,6) and when you are in the GRUB prompt type root (hd0,6). It should work then.

---

