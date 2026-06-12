---
title: "[SOLVED] Partitions"
date: 2007-09-30
forum: General Help
---

### Post by headflux on 2007-09-30
I have a couple of questions:

When opening QT Parted I get an error message which says "No Device found.  Maybe you're not using root user?" I even get this when I have logged in as root using sudo -s in the terminal.  Can anyone tell me what I'm doing wrong?

I want to install XP on a partition so I can play some games I can't get to work in WINE.  My harddisk seems to have 2 partitions already a main C drive and an E drive. I could install on E, but I'm not sure if this is where my Ubuntu build sits. Is there any way to tell?

Can anyone help?

Thanks

---

### Post by x1a4 on 2007-09-30
Run qtparted with root privileges like so: 

gksudo qtparted

---

### Post by headflux on 2007-10-01
Thanks, that worked a treat.  Can anyone help with my second question please?

To put some context, my laptop came preloaded with Vista, and had a recovery partition setup.

When I replaced Vista with Ubuntu, I selected to overide the whole disk, however, I'm now wondering if the Recovery partition was somehow retained.  (Booting from a windows XP cd, it tells me their is an E: partition of approx 2Gig.)

If this E: is the old recovery partition, I could put XP on that rather than creating a new partition.  (I don't need a lot of space for XP as I just want to play a couple of old games that don't work in WINE)

Is there a way to tell what's on that E: partition? and does Ubuntu automatically create a sperate partition just for the OS?

Many Thanks

---

### Post by forestpixie on 2007-10-01
> Is there a way to tell what's on that E: partition? - you should be able to read what's in the partition from within Ubuntu, assuming it's mounted - saying that if you can't see it from there try from within the livecd. I think it's safe to say if you let Ubuntu install to the whole disc in the first place all that could possibly be left that the winxp cd could see would be the recovery partition - not sure why iot didn't take it as well though.

```
does Ubuntu automatically create a sperate partition just for the OS
```

if you didn't create seperate partitions for root, home and swap - it would have installed everything to one partition - and home would be inside root - is that what you're asking?

---

### Post by headflux on 2007-10-02
Thanks Forest Pixie.  E: seems to be the swap partition, with root and home as the other (C:).

Please can anyone advise the safest way to create a new partition?  e.g. that won't destroy my current Ubuntu build. When I use QTParted or GParted, I can see the current partition, but the resize option is greyed out.

Thanks

---

### Post by oldos2er on 2007-10-02
You'd have to boot from the Live CD, or from a gparted cd to resize. You can't do operations like that on a partition you're currently booting from. And make sure the partitions(s) is not mounted!

---

### Post by headflux on 2007-10-02
Thanks Ann.

Sorry for the newb question but how do I check it's unmounted?

---

### Post by forestpixie on 2007-10-02
do it through the livecd - and it shouldn't be mounted- when you run gparted you can unmount if necessary

If you're going to be playing with partitions make sure anything you can't afford to lose is backed up

---

### Post by oldos2er on 2007-10-02
> **headflux said:**
> Thanks Ann.

Sorry for the newb question but how do I check it's unmounted?

 If you're booting the Ubuntu live cd, you'd see an icon on the desktop called "disk" something, or possibly "file system." Right-click on the icon and choose unmount.

---

### Post by headflux on 2007-10-04
I created the partition as per all your advice, which was successful withno data loss - Thanks to all

However, when I installed XP on the new partition, it said it had to deactivate the primary partition (with Ubunutu) to perform the install; but that it could be reactivated from Computer Management, within XP admin tools.

When I go to Computer Management in XP though, the option to reactivate the Ubuntu Partition is grey out, so now I cannot boot my Ubuntu Partition.

Booting again from live CD, I can see my Ubuntu partition and access my data, I just can't boot directly from it.

Can anyone offer any advice/solution?

Thanks

---

### Post by forestpixie on 2007-10-04
I would imagine that XP has overwritten the Ubuntu grub being selfish as it is - although I've never seen a thread with what you've experienced I'm sure someone else has

have a look at these they might help you

fixing grub - [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

supergrub page - [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

recover after windows - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and I'm glad the partitioning went ok :)

---

### Post by headflux on 2007-10-04
Firstly, thank you to everyone who has helped with my problem. 

I think I'm on the home straight, but have hit one more snag.

I fixed the GRUB using of of the links that ForestPixie posted and I can now boot my Ubuntu partition (which is the most important thing), however, the GRUB menu doesn't show XP, so now I can't boot my XP partition.

This is the set of commands I used to fix the GRUB taken from [http://ubuntuforums.org/showthread.php?t=224351:](http://ubuntuforums.org/showthread.php?t=224351:)

Code:

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit

Have I made some error?

Thanks

---

### Post by forestpixie on 2007-10-04
can you do these in a terminal and post the outputs

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
cat /boot/grub/menu.lst
```

---

### Post by headflux on 2007-10-04
Sure, here it is:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11077    88975971   83  Linux
/dev/sda2   *       11078       14264    25599577+   7  HPFS/NTFS
/dev/sda3           14265       14593     2642692+   5  Extended
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    6  FAT16

Disk /dev/sdc: 252 MB, 252051456 bytes
8 heads, 32 sectors/track, 1923 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1923      246093+   6  FAT16
simon@simon-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=12014dde-5477-4f46-a3d6-fabe03dbd066 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cf828c27-688c-43b6-a5bf-a6c97af0c5e4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
simon@simon-laptop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=12014dde-5477-4f46-a3d6-fabe03dbd066 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=12014dde-5477-4f46-a3d6-fabe03dbd066 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=12014dde-5477-4f46-a3d6-fabe03dbd066 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=12014dde-5477-4f46-a3d6-fabe03dbd066 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=12014dde-5477-4f46-a3d6-fabe03dbd066 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

Thanks in advance

---

### Post by forestpixie on 2007-10-04
you need to add in a section to the end of your menu.lst - as I expect you already know.

I'm assuming that you don't want to access your win partition from within ubuntu as it's not in fstab.

we'll backup first 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.0410
```

then open it to edit

```
gksudo gedit /boot/grub/menu.lst
```

put this at the very end of the file below everything else

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Windows XP
root (hd0,1)
makeactive
chainloader +1

that should put the entry in to your menu.lst relating to your win partition on /dev/sda2, at least I hope so :) - I'd be inclined to change the timeout from 3 secs to a bit longer so you can check it out. Have to say I've just taken the windows boot lines from the example, as my win partition is long gone.

Edit - also when you're posting long lists of stuff it makes it a bit easier if you seperate them and put code tags round them

---

### Post by headflux on 2007-10-04
Fantastic, it worked.  Thank you so much. I really appreciate all your help.  

p.s. will do about the code

---

### Post by headflux on 2007-10-04
This Thread is now solved

---

### Post by forestpixie on 2007-10-04
excellent - glad I could help someone close by :)

to mark thread as solved - use thread tools there's an option for you to mark it as solved

---

