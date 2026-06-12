---
title: "GRUB boot not working with other linux and windows"
date: 2007-02-11
forum: General Help
---

### Post by mattgaunt on 2007-02-11
Hey everyone

Im trying to be very awkward and have, ubuntu dapper, egdy, windows xp and windows vista, because of these reasons

1.)I hav dapper setup nicely and im a noob

2.)I want edgy just because it seems like alot of software is working more and there more guides

3.) I hav xp and vista cos i dont trust vista with DRM

Right so here is my set up of hard drives using fdisk -l

> Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       10012    39458816    7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5099    40957686   83  Linux
/dev/hdb2            9332        9729     3196935    5  Extended
/dev/hdb3            5100        9331    33993540   83  Linux
/dev/hdb5            9332        9729     3196903+  82  Linux swap / Solaris

Partition table entries are not in disk order


and this is my GRUB menu.lst at the moment

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		15

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
# kopt=root=UUID=4b74a101-d510-4f52-86c8-1132375ac01f ro
# kopt_2_6=root=/dev/hda1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

Now i want edgy installed on the hdb3 partiation on the hdb drive and have the hda drive as a hard drive for all my music and work files

And at the moment i think edgy is on the hda drive which i really dont want so any ideas how can install edgy on the hdb3 partition cos i tried on the alternate CD and i think it installed but GRUB didnt work and i use edgy live CD and it installs on hda1 but grub works for edgy and nothing else

To be honest if this isnt goin to work or if i need to change the order of hard drives or i just simply need to edit the menu.lst 

Any help would be great, and im really sorry  if im not very clear about anything, im still learning

Thanks alot

Matt

---

### Post by geek_Man on 2007-02-11
You should be able to do that. Can you post what OS's are on what drives and what you *want* the setup to be?

---

### Post by mattgaunt on 2007-02-11
sda1 has windows xp installed on it
sda2 has windows Vista installed on it

hda1 This has edgy installed on it as is the one GRUB boots into I want this one to have all my files on it as ext3 format - and use fs-drivers.org

hdb1 has ubuntu dapper already installed on it
/hdb2 is the Extended drive (Not sure what that means)

hdb3 i want edgy on it but i think it is installed but GRUB is pickin up edgy that is installed on hda1

hdb5 Linux swap / Solaris what ever this is

So i think its just the grub menu.lst that needs changin to except the windows partitions and accept the other edgy that is installed on hdb3

---

### Post by geek_Man on 2007-02-11
Back in the day, there was a limit to how many partitions you could have on a drive, but people realized that they needed more partitions. So they came up with extended partitions which are just partitions within a partition. Swap is kinda like extra ram. You'll have to post what you want a little clearer. If you want to add Windows to your boot menu, that can be done.

---

### Post by mattgaunt on 2007-02-11
I want windows xp from sda1, windows vistafrom sda2, ubuntu edgy from hdb3, ubuntu dapper from hdb1 on the grub boot

Just it seems there is no way of gettin grub to scan my current set up and working it all out from there so im guessing i hav to do it manually but im not sure how to go about it because i want to use hda1 as a hard drive to hold my files so i guess i shud make the linux hard drive the master and the hda as my slave drive

But any ideas how i can get my grub boot to recognise all my OS's??

---

### Post by geek_Man on 2007-02-11
Okay, I just realized that you don't actually want to move your Ubuntu and Windows installs around, you just wanted them in the menu (I think). You can add entries for your other OS's in your menu.lst file. Just so that we're clear, what's on hda1? Is that like backup or what?

---

