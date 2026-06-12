---
title: "Grub multibooting and Error 21"
date: 2007-11-05
forum: General Help
---

### Post by drguerra on 2007-11-05
Okay, so I have Vista and Ubuntu 7.10 (both 64 bit versions) installed on my master IDE drive. When my computer boots, the GRUB menu will appear. I have three options. Ubuntu 7.10, Vista and XP. Ubuntu and Vista boot fine, however, XP will not boot properly. I click XP and it will say:
      Error 21: Selected disk does not exist. 

So, what am I do to? I actually had it triple booting perfectly before, so I know it CAN work for sure.

IDE drive with Vista/ubuntu boots into GRUB, SATA with XP on secondary. If I change in bios to boot from the SATA drive, XP boots up no problem with no grub menu.

I did 
cat /etc/fstab

and these are the results:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c8912891-39fc-4224-8ff5-37bd3980940d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=20c97b02-d219-4e63-83d2-50f91b6b9b88 /home           ext3    defaults        0       2
# /dev/sda4
UUID=6018F68018F6550E /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=DCF8B0BCF8B0966C /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=1369f883-69c4-4790-a37c-b631479f6e34 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


and then I did this
cat /boot/grub/menu.lst

results:

 menu.lst - See: grub(8), info grub, update-grub(8)
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
default         0

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
# kopt=root=UUID=c8912891-39fc-4224-8ff5-37bd3980940d ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c8912891-39fc-4224-8ff5-37bd3980940d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c8912891-39fc-4224-8ff5-37bd3980940d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Windows Vista/Longhorn (loader)
root            (hd0,3)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


I really hope the above info helps and saves time. I would appreciate help greatly! By the way, I'm VERY new to Linux, so don't make assumptions that I know what you're talking about! 

Thanks again!

---

### Post by logos34 on 2007-11-05
looks like the gutsy installer got all the entries correct.  

Your /boot/grub/device.map should read:

> (hd0) /dev/sda
(hd1) /dev/sdb

go into the bios... the hard drive controller detect settings for XP disk should be set to "auto".

[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

-or try changing root line in XP entry to:

> rootnoverify (hd1,0) 

---

### Post by drguerra on 2007-11-05
Unfortunately, I did both of those and still the same problem. I also read all the documentation you linked, and that didn't help either. Tried Super Grub, no help.

Okay, so I'm booting using an IDE drive that is set as primary slave, and I have my SATA plugged into SATA1. Should I make the IDE drive master and put the SATA drive into an SATA2 slot?

Would that help at all?

I know I got it to triple boot without unplugging/replugigng anything, and I honestly don't know why it won't work now.

---

### Post by meierfra on 2007-11-05
Deleted (Hadn't read the posts careful enough)

---

### Post by logos34 on 2007-11-05
> **drguerra said:**
> Unfortunately, I did both of those and still the same problem. I also read all the documentation you linked, and that didn't help either. Tried Super Grub, no help.

Okay, so I'm booting using an IDE drive that is set as primary slave, and I have my SATA plugged into SATA1. Should I make the IDE drive master and put the SATA drive into an SATA2 slot?

Would that help at all?

I know I got it to triple boot without unplugging/replugigng anything, and I honestly don't know why it won't work now.

oh, I thought it was master...But if you say that setup worked before then it shouldn't be the issue. Frankly, I'm out of ideas.  You've tried everything else to my knowledge, so you might as well try different connectors/channels.  

But before you do that try this XP entry:

> title Microsoft Windows XP Home Edition
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

Maybe the fact that it's slave (or the cd/dvd is connected on same cable as master?) is causing the bios and grub some confusion, even though it got the entry right on installation.  dunno.  

post your fdisk and hardware listing:

[B]sudo fdisk -l

sudo lshw -C disk[/B]

---

