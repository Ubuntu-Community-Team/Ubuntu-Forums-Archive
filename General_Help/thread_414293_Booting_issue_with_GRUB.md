---
title: "Booting issue with GRUB"
date: 2007-04-19
forum: General Help
---

### Post by Babelfish on 2007-04-19
Okay, I'm completely new to linux. I installed Ubuntu 6.10 in a dual boot along with XP Pro last week. I have three drives, 1 has XP, 1 has Ubuntu and one is storage. After getting Ubuntu up and running I started trying to update stuff. I downloaded the latest drivers for my vid card (Geforce 7950 GT) from nVidia and attempted to install them following instructions here and on the nVidia site. Somehow while doing this I managed to break X. Left with just the terminal and no UI and new to linux, I just formatted and reinstalled as there was no way I was going to be able to fix it from the terminal.

After reinstalling and attempting to boot from GRUB I received Error 17: Unable to mount the selected partition.

My partition table is thus..

hd0,0 XP system files
hd1,0 Ubuntu root
hd1,1 Ubuntu swap
hd1,2 Ubuntu /home
hd1,3 Ubuntu fat32 partition for storage
hd2,0 NTFS storage and, oddly enough, the boot sector for XP due to my odd Windows install that I'm too lazy to fix

Editing the Ubuntu option in GRUB yields..

root: hd0,0
kernel: /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd: /boot/initrd.img-2.6.17-10-generic

I changed root to hd1,0 and it starts to boot but hangs as soon as it hits the loading screen.

Any advice?

---

### Post by Babelfish on 2007-04-20
Bump.

---

### Post by confused57 on 2007-04-20
Boot the live cd, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by Babelfish on 2007-04-20
```

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406   83  Linux
/dev/sdb2            1276        5099    30716280   83  Linux
/dev/sdb3            5100        5132      265072+  82  Linux swap / Solaris
/dev/sdb4            5133       30401   202973242+   b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS
```

---

### Post by confused57 on 2007-04-20
> **Babelfish said:**
> ```

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406   83  Linux
/dev/sdb2            1276        5099    30716280   83  Linux
/dev/sdb3            5100        5132      265072+  82  Linux swap / Solaris
/dev/sdb4            5133       30401   202973242+   b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS
```

Highlight your Ubuntu entry in the boot grub menu, press "e", change root to (hd1,0), and in the kernel line change to root=/dev/hdb1, then press "b" to boot.

If this doesn't work you might want to mount your root partition using the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb1 /media/ubuntu
```

then you might want to post the following:
```
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
gedit /media/ubuntu/etc/fstab
```

What is your hard drive boot order in bios?

---

### Post by Babelfish on 2007-04-20
> **confused57 said:**
> Highlight your Ubuntu entry in the boot grub menu, press "e", change root to (hd1,0), and in the kernel line change to root=/dev/hdb1, then press "b" to boot.
After doing this it still hangs at the loading screen.

> **confused57 said:**
> 
If this doesn't work you might want to mount your root partition using the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb1 /media/ubuntu
```

then you might want to post the following:
```
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
gedit /media/ubuntu/etc/fstab
```

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb1 /media/ubuntu
mount: special device /dev/hdb1 does not exist

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /media/ubuntu
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
# kopt=root=UUID=1fcf7b9d-15c2-4bce-a5df-130c7aa83cc7 ro
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```
```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1fcf7b9d-15c2-4bce-a5df-130c7aa83cc7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=310d8ea4-fbf1-41e5-ae2a-41259c940db0 /home           ext3    defaults        0       2
# /dev/sda1
UUID=BE88BED188BE8783 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=26E002B4E0028A6F /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb4       /media/shared   vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=73c9e46c-a13d-46c5-8c3f-44953083ff50 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
> **confused57 said:**
> 
What is your hard drive boot order in bios?
GRUB is on sda1 so that's first when I'm working with this. GRUB doesn't load Windows properly (I'm assuming this is due to the aforementioned weirdness with the boot sector being on a separate drive from the system files.) so I switch sdc1 back to first priority to boot back into Windows.

---

### Post by Babelfish on 2007-04-20
Well I got it to work. :)
> 
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb1 /media/ubuntu
mount: special device /dev/hdb1 does not exist

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /media/ubuntu

This tipped me off.

I changed it to hd1,0 and root=/dev/**s**db1 and it booted up perfectly. Thanks for pointing me in the right direction.

---

### Post by confused57 on 2007-04-20
> Highlight your Ubuntu entry in the boot grub menu, press "e", change root to (hd1,0), and in the kernel line change to root=/dev/hdb1, then press "b" to boot.

My mistake, I was in a hurry...have you tried root=dev/sdb1, using the above method.

This "should" boot your Windows from grub:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

You might also want to download a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

it's a small download & may be able to boot your Ubuntu drive

Added:  You beat me too it,  good job.

---

### Post by confused57 on 2007-04-20
In addition to making all the changes permanent in your /boot/grub/menu.lst, you need to check the #kopt & #groot  lines:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

If it's UUID in the kopt line, you should be fine...if not, you need to change it to reflect sdb1 or a kernel update will change your kernel root entries to how it's listed in this line.

---

### Post by Babelfish on 2007-04-20
# kopt=root=UUID=1fcf7b9d-15c2-4bce-a5df-130c7aa83cc7 ro
# kopt_2_6=root=/dev/hda1 ro

I'm guessing I should switch that hda1 to sdb1?

---

### Post by confused57 on 2007-04-20
> **Babelfish said:**
> # kopt=root=UUID=1fcf7b9d-15c2-4bce-a5df-130c7aa83cc7 ro
# kopt_2_6=root=/dev/hda1 ro

I'm guessing I should switch that hda1 to sdb1?

Yes, that "should" work.

---

