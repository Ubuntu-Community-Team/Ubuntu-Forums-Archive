---
title: "Help I can't boot my system! Error 15: File not found"
date: 2007-06-02
forum: General Help
---

### Post by bone2006 on 2007-06-02
Grub is giving me Error 15: File not found


I originally started out with windows XP and I had two NTFS partitions, once I had a dual boot ubuntu system I used gparted and created another ext3 partition.  
Therefore I had 2 NTFS partitions and 2 EXT3 partitions.   

After months and months of using ubuntu I decided I just need to get rid of my windows and NTFS partition.  First I started out and removed the C: windows partition, rebooted into ubuntu and everything was alright.   Then I went into my last NTFS partition that windows calls D:, I copied everything over to my ext3 partition that is not in root and has home there.

So now I was ready to get rid of the last NTFS partition, so I removed the NTFS partition that only had data(not windows) and resized/increased my other parititions with gparted.

When I rebooted I got the message, which seems to come from Grub
Error 15: File not found

I tried booting up the livcd and seeing if I could edit grub or do something, but I can't seem to figure out what to do or if it's something else?

Any help is greatly appreciated

---

### Post by CaveRat on 2007-06-02
It sounds like you deleted your Grub boot loader. If I'm wrong, I'm sure someone will come along and correct me. In the mean time, check out this link to see if it might perhaps fix you problem.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=224351&highlight=dual+boot)

---

### Post by bone2006 on 2007-06-02
Sorry if I didn't state this before, but the menu.lst file is still there and I was trying to edit it.  Seems the grub directory and eveything is still there.  I'll look at the link and see if that can get me back up and running.
Thanks for the link

---

### Post by confused57 on 2007-06-02
> **bone2006 said:**
> Sorry if I didn't state this before, but the menu.lst file is still there and I was trying to edit it.  Seems the grub directory and eveything is still there.  I'll look at the link and see if that can get me back up and running.
Thanks for the link
Boot the live cd, from a terminal, post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L", you probably already know this

Here's how to mount your root partition in the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
you might also want to post your /boot/grub/menu.lst

Your UUID's have probably changed on the filesystems of the partitions that you resized, so you'll need to use the command:
```
blkid
```
to determine the new UUID's

The link above shows how to edit your /etc/fstab after mounting your root partition...you can probably just copy & paste the new UUID's from "blkid" into your /etc/fstab.

---

### Post by bone2006 on 2007-06-02
Thanks for the reply, I ended up moving my home directory to so many partitions and doing so many things with my system that In finally just decided to blast away the main root directory and reinstall the OS again.  Back up and running

Thanks for taking the time out to help though
very much appreciated

---

### Post by LitusMayol on 2008-07-08
Hi!

I'm having the same exact problem with my **Ubuntu**, the "*Error 15: file not found*". 

I've also installed a  **XP** and **UbuntuStudio**. By the way I can run the **UbuntuStudio**, but I'd like to run again the other. CAn any one help?


Perhaps my *menu.lst* is useful, here it is:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		6

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
# kopt=root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		UbuntuStudio
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		UbuntuStudio (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		UbuntuStudio (generic)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

#title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04, kernel 2.6.24-18-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-rt
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-18-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-18-rt

#title		Ubuntu 8.04, kernel 2.6.24-18-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04, kernel 2.6.24-16-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-rt
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-16-rt

#title		Ubuntu 8.04, kernel 2.6.24-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd0,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro quiet splash locale=ca_ES 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu generic 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro quiet splash locale=ca_ES 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
#title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda4)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro single 
#initrd		/boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
#title		Ubuntu 8.04, memtest86+ (on /dev/sda4)
#root		(hd0,3)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot

```


Thanks in advance

---

