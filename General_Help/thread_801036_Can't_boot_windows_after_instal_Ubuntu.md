---
title: "Can't boot windows after instal Ubuntu"
date: 2008-05-20
forum: General Help
---

### Post by Betse on 2008-05-20
A few weeks ago i installed 8.04 over a 7.10 install. With ubuntu everything is fine, however I also have a windows XP install which I use to play games and so on.
Since the Ubuntu install the windows install isn't reachable any more because of a 'NTLDR is missing' message. I tried the googled guides to solve this problem but nothing worked.
I tried reinstalling windows but off course my Grub got overwritten so I only had Windows. I got Grub back by booting a live-disk and running Grub.
Now I can boot Ubuntu but windows gives me the same message about the NTLDR. I tried editing the Grub loader, but nothing worked.

Here are my menu.lst and fdisk -l

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
# kopt=root=UUID=e2d47a43-a4bf-4f6d-87a6-08f2520839bf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e2d47a43-a4bf-4f6d-87a6-08f2520839bf ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e2d47a43-a4bf-4f6d-87a6-08f2520839bf ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify            (hd1,0)
savedefault
makeactive
chainloader     +1
boot
```
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd37fa4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       24792   172923660    f  W95 Ext'd (LBA)
/dev/sda5            3265       24792   172923628+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfca143eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          33      265041    7  HPFS/NTFS
/dev/sdb2              34        1278    10000462+  83  Linux
/dev/sdb3            1279        1776     4000185   82  Linux swap / Solaris
/dev/sdb4            1777       38913   298302952+  83  Linux

```

Looking through this forum and internet I found some people with comparable problems, but the solutions posted there didn't work for me.
Is there somebody who has another idea?

---

### Post by Betse on 2008-05-21
I hope I made it clear that I already tried some things (that's why I posted the menu.lst and fdisk -l output).
Isn't there anybody who is willing to help me out?

---

### Post by LeGollemux on 2008-05-21
I tend to do this kind of thing quote a bit. One of problems I encountered was when your XP partition is a dynamic partition.If thats the case you need to set it back to being a basic partition. If thats not the case then what I normally use when backed into this particular corner is "Super Grub Repair" disk. It fixes grub and has a go at fixing windows partitions.

---

### Post by Betse on 2008-05-22
The problem can be that I have linux on a sata drive and windows on a ide drive. For some reason windows had to install something on the sata drive to make a windows install on the ide drive work (that's why there is a 256mb small drive on sdb).
Is that what you mean by a dynamic partition?

---

### Post by gkestrel on 2008-06-15
When you have ide and sata drives mixed you can often run into problems like this. Grub often can get the two drives mixed up when it is installed.

First try editing /boot/grub/menu.lst first go to the windows entry at the bottom of the file, try changing it from this

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify            (hd1,0)
savedefault
makeactive
chainloader     +1
boot

to this

title		Windows 
root		(hd1,0)
#rootnoverify            (hd1,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1
#boot

save and reboot and see if it works. Please let me know if this is successful or not, if not i will try and help you further

---

### Post by Betse on 2008-06-25
No this doesn't work unfortunately. After booting that option a blinking cursos appears. It doesn't even react to CTRL-ALT-DEL.

The supergrub !WIN! :((( option does work, I use the disk everytime I want to boot into windows. Which is not that often, but if Supergrub can do it, than a boot option should be able to do it aswell.
I however can't find what that option actually does.

---

### Post by meierfra. on 2008-06-25
try

title Windows XP
root (hd0,0)
chainloader +1

---

### Post by Betse on 2008-06-25
Nope that also doesn't work. 
I also noticed that the line:
root (hd0,0) does not show up when i try to edit the boot option on startup. A Bit strange if you ask me.

---

### Post by CrusaderAD on 2008-06-25
Install windows like you normally would. Then just run your linux off a flash drive. Any linux you want. As long as your bios let you boot to your flash drive. [www.pendrivelinux.com](www.pendrivelinux.com) will help you avoid all these problems. Or you can buy one of those switches which allows you to switch certain drives on and off, but you lose the ability to have both at once.

---

### Post by Betse on 2008-06-25
I can boot linux normally with Grub. And when I use the fixmbr function of windows i can boot windows normally.
Since I use linux more, I always use Grub.
For windows I use the Supergrub disc Win :(((( option. Does anyone know what that function actually does?

---

### Post by meierfra. on 2008-06-25
> 
I also noticed that the line:
root (hd0,0) does not show up when i try to edit the boot option on startup. A Bit strange if you ask me.

Strange indeed.  Did you double check "menu.lst"?  Maybe you have a typo.

Any error messages?



Try this:  Add the Grub menu at startup, press "c". Then at the "grub" prompt:

root (hd0,0)

chainloader +1

boot

---

### Post by meierfra. on 2008-06-25
> For windows I use the Supergrub disc Win ((( option  Does anyone know what that function actually does? 

It does 

root (hd0,0) 
chainloader +1
boot

So that's why I'm really surprised that my suggestion did not work.

---

### Post by Betse on 2008-06-25
Hmm ok, I'll try the c option in grub in a few minutes.

---

