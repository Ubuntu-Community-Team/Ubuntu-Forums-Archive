---
title: "[SOLVED] GRUB Error 21"
date: 2007-08-16
forum: General Help
---

### Post by 0micron on 2007-08-16
Hello,

I'm quite new to Linux (one month) and tried to fix all the problems I got so far, but am stuck with this one. I have two hard drives, one for Windows XP and the second one dedicated to Ubuntu. I installed everything and the installation went fine, but then I got this error message when I botted up the system the next day. I thought I messed something up during installation, so I reinstalled Ubuntu, but I got the same error message again:

GRUB loading stage 1.5
GRUB loading, please wait...
error 21

And then nothing happens. If I reboot the system GRUB loads fine and no matter how many times I reboot, it goes through. The error only comes up after shut down.

I read other posts about similar issues, but couldn't find the problem. I thought these might be useful:

**menu.lst**

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
default		saved

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
# kopt=root=UUID=61a8851d-e470-4f21-8aef-e93fa06e4774 ro

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
 howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu 7.04
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=61a8851d-e470-4f21-8aef-e93fa06e4774 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=61a8851d-e470-4f21-8aef-e93fa06e4774 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=61a8851d-e470-4f21-8aef-e93fa06e4774 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=61a8851d-e470-4f21-8aef-e93fa06e4774 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
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

**device.map**

```
(hd0)	/dev/hda
(hd1)	/dev/hdb
```

**fdisk -lu**

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    58556924    29278431   83  Linux
/dev/hdb2        58556925    60050969      747022+   5  Extended
/dev/hdb5        58556988    60050969      746991   82  Linux swap / Solaris

```

---

### Post by frodon on 2007-08-16
Meaning of error 21 :
> 21 : Selected disk does not exist. This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.First i would remove the boot flag on the windows partition (hda), you can do this either with windows using partition magic or with your ubuntu live CD using gparted.
Then check in your BIOS configuration that your computer boot first on your linux drive (hdb2).

---

### Post by 0micron on 2007-08-16
I removed the boot flag from the windows drive using gparted and tried a few combinations in the BIOS boot order, but couldn't fix it that way. When I choose to boot from "HDD 1" I get "Operating system error" before GRUB loads. If I choose "HDD 2" and above it says there's no operating system and with "HDD 0" it's the same stuff as explained in the first post - after shut down goes to error 21 and when I reboot goes through.

Any other suggestions? :-?

---

### Post by frodon on 2007-08-16
Your device.map and menu.list are ok for me so next test would be, if you agree, to reinstall grub on hdb.

1- Boot your liveCD.
2- open a terminal and type :
```
sudo grub
```
3- then once in the grub terminal type :
```
root (hd1,0)
setup (hd1)
quit
```
Full and detailed instructions here (quick start section):
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
4- Reboot

I think that maybe GRUB has been installed on the wrong disk.

---

### Post by 0micron on 2007-08-16
Reinstalled grub as you said:

```
grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

```

Then I rearranged the boot order to boot first from HDD 1, this time it showed me the welcome GRUB screen (where you choose operating system), but when I chose either Ubuntu or Windows I got an error:

Error 17: Cannot mount selected partition
Press any key to continue

When I press any key I see the welcome screen again and this goes on and on. 

If I boot from "HDD 0" it's like before reinstalling GRUB.

---

### Post by frodon on 2007-08-16
ok so it's what i guessed GRUB has been installed on the wrong drive at the install so you have GRUB installed on both drives (not a big issue).

meaning of error 17 :
> 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

In most of the cases reinstalling GRUB solve the error 17, could you please check booting the liveCD and opening a grub terminal (sudo grub) that the result of the command "find /boot/grub/stage1" is hd1,0.

---

### Post by 0micron on 2007-08-16
Yes
```

grub> find /boot/grub/stage1
 (hd1,0)

```

---

### Post by frodon on 2007-08-16
Arg, we are not far, the error 17 is not a big issue but it is sometimes a bit annoying to figure out where is the wrong parameter.
Could you post here the content of your fstab file (it is under /etc), i guess your menu.lst and device.map file didn't change so ne need to post them again.

---

### Post by 0micron on 2007-08-16
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=61a8851d-e470-4f21-8aef-e93fa06e4774 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb5 :
UUID=4eeff90c-aef5-4577-abcc-1580352c1056 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0


```

I had a quick look at device.map and menu.lst and they seem to be the same.

---

### Post by Herman on 2007-08-16
Hello 0micron and frodon
Excuse me for interjecting, but I was thinking that maybe it could be that your BIOS, 0micron, is having trouble deciding which disk is first and which one is second?

If you have an IDE hard drive cable with a black plug that plugs into the motherboard and black plugs that plug into each hard drive you should check your hard disk jumper settings and make sure one hard disk has its jumpers set to 'master' position, and the other has the jumper set to identify it to the BIOS as the 'slave' hard drive.

If you have an IDE hard drive cable that has a blue end plugged into the motherboard and one gray and one black plug, you have a 'cable-select' IDE cable. The jumper settings need to be both set to 'cable select'. Whichever hard drive is plugged in with the black plug will be master, or number 1 hard drive and whichever is plugged in with the grey plug will be slave, or number 2 hard drive.

It's worth a look anyway,
Regards, Herman :)

---

### Post by 0micron on 2007-09-24
Hi guys,

Thanks for the help. It turned out the problem was one of the hard drives was connected as Cable Select, while the other one had no jumpers at all :) Anyways, when I changed the jumper settings from Cable Select to Master, it worked fine (the other drive still has no jumpers, though). 

Regards

---

### Post by frodon on 2007-09-24
Great :KS

Thanks for the update 0micron, i'm glad all is working for you now.

---

