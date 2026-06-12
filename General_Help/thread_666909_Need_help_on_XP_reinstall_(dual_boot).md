---
title: "Need help on XP reinstall (dual boot)"
date: 2008-01-13
forum: General Help
---

### Post by tkrisz on 2008-01-13
Hello!
Currently I have an XP and an old 64 bit Ubuntu on my IDE (PATA) drive. And a 7.10 Ubuntu (32 bit) install on my bigger SATA drive.
I want to clear the PATA drive from the 2 OS and reinstall XP on the whole drive.
I already moved all important data to my SATA drive.
As i know i will lose my GRUB after the install and i have to remake it by the help of the  live CD.
So i have 3 questions.
1, Should i do anything before i put in the XP install CD? I mean is it enough if i clear the drive with whatever the XP CD offers?
2, Is there any issues with the different type of drives (PATA, SATA)?
3, Can someone give me a line-by-line instruction what should i type after typing "sudo grub" into the terminal of the live CD? I know roughly, but i would like to be 100% sure. I fear that i will do something wrong. Here's my /boot/grub/menu.lst.

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage=(hd1,5)/boot/grub/splashimages/53373-NightOfUbuntu.xpm.gz

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
# kopt=root=UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional - magyar
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-amd64-generic (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-amd64-generic (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-amd64-generic (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by PmDematagoda on 2008-01-13
Your menu.lst looks good, so you will not need to make any critical further changes with the new XP install, but you can remove the entries for the older Ubuntu x64 install so that the GRUB list looks cleaner.

But since the MBR will be overwritten by XP's boot-loader you would have to reinstall GRUB back to the MBR, you can do that using [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download").

> 1, Should i do anything before i put in the XP install CD? I mean is it enough if i clear the drive with whatever the XP CD offers?
The XP CD does enough, just format the entire HDD and reinstall it.

> 2, Is there any issues with the different type of drives (PATA, SATA)?
There are certain situations where GRUB could be confused, but it obviously did not because you managed to dual-boot Ubuntu and XP.

---

### Post by yabbadabbadont on 2008-01-13
I would disconnect the SATA drive beforehand.  The various Windows installers that I have used over the years have a tendency to arbitrarily decide to remove unknown partition types.  (Even from secondary drives)  Better safe than sorry.  ;)

---

### Post by Victormd on 2008-01-14
> **tkrisz said:**
> Hello!
Currently I have an XP and an old 64 bit Ubuntu on my IDE (PATA) drive. And a 7.10 Ubuntu (32 bit) install on my bigger SATA drive.
I want to clear the PATA drive from the 2 OS and reinstall XP on the whole drive.


What is your reason for installing a fresh XP? Have a clean Windows or simply have XP on one drive and Ubuntu on the other? If your intention is to have a clean XP, insert the CD, format the PATA drive, you might want to physically remove the SATA to be on the safe side but it's not necessary because with the XP installer, you can clearly see the drives and select the ones to delete. Now if you simply want to have XP on one HD and Ubuntu on the other, use something like PQ-Magic toremove your old 64 bit Ubuntu partition and resize the XP partition to fit the entire HD. This will save you some time installing all the softs again and you won't have to worry about the GRUB messing up. You would just need to modify your boot list to clean it up.

---

### Post by tkrisz on 2008-01-21
Thank you for the help. Everything went ok except for this one:

At booting Ubuntu the process stops and gives me  a root prompt.
It tell me that there's an error with fsck and i should manually solve this.

It tells me that i will find the info in the /var/log/fsck/checkfs file:

```

Log of fsck -C -R -A -a 
Mon Jan 21 11:49:51 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=beffbfd3-3e8a-4636-9364-04470045fa52'

fsck died with exit status 8

Mon Jan 21 11:49:51 2008
----------------

```

If i type exit the boot process continues and everything seems ok.

---

### Post by torgrot on 2008-01-21
When you deleted partitions, I would guess the Ubuntu 64, it is trying to run fsck on a partition that no longer exists.  Edit the /etc/fstab to remove the entry for that partition.

torgrot

---

### Post by tkrisz on 2008-01-21
Thanks!

```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=88C85F95C85F807C /media/hda1 ntfs-3g defaults,locale=hu_HU.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=beffbfd3-3e8a-4636-9364-04470045fa52 /media/hda2 ext3 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=abefe60e-1ced-4850-b325-6fa71e2c9213 none swap sw 0 0
# Entry for /dev/sda5 :
UUID=4106b847-e9fb-42b2-b269-73dd452cce38 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/WinXP ntfs-3g defaults,locale=hu_HU.UTF-8 0 0
```

I think i should delete these 6 lines:
```

# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=88C85F95C85F807C /media/hda1 ntfs-3g defaults,locale=hu_HU.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=beffbfd3-3e8a-4636-9364-04470045fa52 /media/hda2 ext3 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=abefe60e-1ced-4850-b325-6fa71e2c9213 none swap sw 0 0
```
Is that ok?

---

### Post by PmDematagoda on 2008-01-21
Could you please provide the output of:-
```
sudo fdisk -l
```

---

### Post by tkrisz on 2008-01-21
sudo fdisk -l

```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa152a152

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf2bc

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24439   196306236    5  Kib&#337;vített
/dev/sda5               1         124      995967   82  Linux swap / Solaris
/dev/sda6             125       24439   195310206   83  Linux

```
half English, half Hungarian  :-)

---

### Post by torgrot on 2008-01-21
> **tkrisz said:**
> Thanks!

```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=4fc206d8-b91c-4cfa-a1b5-8d44fd1400d3 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=88C85F95C85F807C /media/hda1 ntfs-3g defaults,locale=hu_HU.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=beffbfd3-3e8a-4636-9364-04470045fa52 /media/hda2 ext3 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=abefe60e-1ced-4850-b325-6fa71e2c9213 none swap sw 0 0
# Entry for /dev/sda5 :
UUID=4106b847-e9fb-42b2-b269-73dd452cce38 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/WinXP ntfs-3g defaults,locale=hu_HU.UTF-8 0 0
```

I think i should delete these 6 lines:
```

# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=88C85F95C85F807C /media/hda1 ntfs-3g defaults,locale=hu_HU.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=beffbfd3-3e8a-4636-9364-04470045fa52 /media/hda2 ext3 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=abefe60e-1ced-4850-b325-6fa71e2c9213 none swap sw 0 0
```
Is that ok?
Yes, those would have been the second, third and swap partition on the first hard drive.  Those are the ones I would delete.  

torgrot

---

### Post by tkrisz on 2008-01-22
Thanks. Now the boot process seems ok. But now can't set  ntfs-3g. (Or at least the icon of my  Windows partition disappeared.). Previously it seemed ok.
If i run the configuration tool the partition list does not appear, just asks if i want to enable write support for internal/external device.

Edit: Mysterious. Now the icon is there. Didn't even logged out.

---

### Post by Big_Rog on 2008-03-04
I've got an existing Ubuntu installation, and would like to add XP to a second drive, much like this fellow has done.  I haven't tinkered with GRUB before, but from[ another post]("http://ubuntuforums.org/showthread.php?t=685846") in the forums here it can be a bit tricky to sort out which drive ID is which, i.e. hdd(0,0) vs hdd(1,0).  Would someone be kind enough to point out what commands would be needed to get GRUB in order?  A how-to at [apcmag.com]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp") covers single drive install commands for GRUB and menu.lst, but not dual-drive.

Also, is moving my linux install from sda1 to sdb1 (putting windows drive physically first--and I can't pick which SATA drive to boot from first) going to break some settings, i.e. swap file assignment and UUIDs?  I ran amok of the "no swap file after hibernate" problem last summer and know a bit of the hassle of getting those UUID associations back in line with fstab or whatnot.

*edit*
Some more googling came up with [this old thread]("http://ubuntuforums.org/archive/index.php/t-615929.html") and it looks pretty straightforward as far as getting fstab and menu.lst back in order with the new UUID.  Thankfully linux seems to be more intelligent about not using hardcoded drive assignments in software installations than windoze.

*UPDATE*
Ok, things went very smoothly. 
*  Installed windows on the new drive with the ubuntu disk not mounted to preserve the C:\ install for windows.
*  Ubuntu was already booting up as sdb (had the new drive mounted on the first SATA channel by accident, but initramfs was able to cope with a reboot or two) so the fstab was straight. 
*  My BIOS allowed me to pick which SATA drive to boot first, so i could get back to a working OS either way if one went sour.
* Your /boot/grub/menu.lst needs to be updated to show that ubuntu is now on the second hard drive channel, so all the kernel "root   (hd0,0)" need to be changed to the new location, i.e. (hd1,0) and the windows root as (hd0,0).  Booting from a live CD will get you to a working editor, but you can't just 'sudo gedit /boot/grub/menu.lst" as the tutorial implies: you're mounted from the CD, not the HD (remember, GRUB doesn't know where your disk is mounted yet).  Some users have reported getting a blank file for menu.lst, and i suspect this to be the cause.  Navigate all the way to the top of the file system, then go to media/boot/grub/ to get to menu.lst. Reboot and all should be dandy!
* The tutorials on apcmag were pretty accurate, but a few minor version differences could cause a complete novice user to get stuck.

*update to update*
* I sometimes get a hang on boot that stalls the splash screen, then drops to text with a prompt of:
```
 (initramfs)
```
rebooting sometimes works, sometimes it doesn't.
* I also changed the fstab device IDs to actual /dev locations instead of UUID.  not sure if that helped, but after i did i got a clean boot once, and random hangs.

---

