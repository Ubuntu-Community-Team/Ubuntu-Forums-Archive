---
title: "Suspected GRUB error"
date: 2007-06-13
forum: General Help
---

### Post by jtreach on 2007-06-13
I was using Grub to select which partition to load (I am dual booting windows xp and ubuntu feisty) but I just tried to boot up and got the message "Please select boot drive, or insert boot media" (or something to that effect) the only thing I could think of doing was to insert the ubuntu live cd (which has worked hence me typing this) but this is only temporary (I can't work by live booting the installation disk pernamently).

Has anybody got any suggestions? I am not incredible technically skilled (I can do very extremely basic command line task, and am comfortable with the ubuntu gui)

Thanks in advance, JT

---

### Post by merlinus on 2007-06-13
Did the grub appear?

Please post the output of this terminal command:

```

sudo fdisk -l

```

(l is a lowercase L)

It may offer useful information.

-merlin

---

### Post by jtreach on 2007-06-13
GRUB did not appear. The output of the command you mentioned are below:

sudo fdisk -l

```
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10836    87040138+   7  HPFS/NTFS
/dev/hda2           10837       24438   109258065   83  Linux
/dev/hda3           24439       24792     2843505    5  Extended
/dev/hda5           24439       24792     2843473+  82  Linux swap / Solaris

```

The menu.lst file contained nothing.
The fstab file contained the following:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

---

### Post by merlinus on 2007-06-13
> 
The menu.lst file contained nothing.
The fstab file contained the following:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0


This is because it is looking for those in RAM, not on your hard drive.

You can mount your linux partition this way:

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda2 /media/ubuntu

```

Then open Nautilus (file browser), and navigate to /media/ubuntu.  You should be able to find /boot/grub/menu.lst and /etc/fstab.

If that fails, then try super grub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by logos34 on 2007-06-13
> The menu.lst file contained nothing.
The fstab file contained the following:
Code:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

That's from the CD, not your hard drive.  You need to mount the partiton to access your files.

Sounds like you didn't set the bios boot order back to start from the hard disk and it's still booting first to the cdrom, but if it was empy normally it should proceed to boot the next device.  Double check your bios settings.
Maybe it's no longer detecting the hard drive for some reason. 

If you manage to get the grub menu to come up, but can't get it to boot into linux, hit the 'e' key to show the path to the kernel.  The 'root' line should read 'root (hd0,1)', aka hda2.  Change if necessary.  Make the change permanent when you get into ubuntu.

edit: or try SuperGrub like merlinus suggested.  It's a neat utility.

---

### Post by jtreach on 2007-06-14
Okay the proper output from the grub menu.lst file (from my hard drive) is:

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
# kopt=root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

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

```

And the proper output (again after mounting the hard drive) from the fstab file is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4d5ebc22-68db-4187-a07f-8cbbd4230d27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=668465a6-d54a-4623-8ac0-7bec86029253 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

Any good?

---

### Post by confused57 on 2007-06-14
Your menu.lst & fstab looks OK...you might try running this command, using the live cd:
```
blkid
```
compare the UUID results to your menu.lst/fstab UUID's

You could try reinstalling grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If this fails, you could try restoring Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
the easiest way is to boot up Window's install cd(not a recovery cd), enter recovery console by pressing "r", then run the command, FIXMBR...if you don't have a Window's install cd, you would need access to another computer that you could make a copy of the Super Grub Disk.

Do you remember what you might have been doing(installing, reconfiguring,etc) just before you started having the problems?

---

### Post by jtreach on 2007-06-14
After reinstalling Grub everything is working fine.... I had installed gpartion and as I was intending to resize my partition, but I hadn't done anything with it (as far as I could tell) although I did notice that it seemed to have mounted my ntfs partition (windows) when I ran it....

That and installed EAC under wine were the last things I did.

Thanks alot another one of my problems solved by the great ubuntu community! :)

---

