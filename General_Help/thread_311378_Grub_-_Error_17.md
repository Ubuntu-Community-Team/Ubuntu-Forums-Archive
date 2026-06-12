---
title: "Grub - Error 17"
date: 2006-12-02
forum: General Help
---

### Post by rubikfreak on 2006-12-02
I'm running Windows right now and I had a separate computer for Ubuntu. My dad took the Ubuntu computer to make it a media center/server, so I decided to dual boot on my Windows machine. I have 4 drives, 1 IDE and 3 SATA. Windows was on the IDE drive and the rest of the drives had unallocated space, so I booted up the livecd for Ubuntu Edgy 6.10 and the installed to the first SATA drive. When I rebooted, I got the usual grub screen, and I tried to boot into Ubuntu. Grub failed with error 17. I can still boot to Windows though. Any help with this will be very much appreciated! :)

---

### Post by Sef on 2006-12-02
Grub Error 17 from the GRUB manual:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

What file system did you use for Ubuntu?

---

### Post by bulldog on 2006-12-02
It could be that GRUB is pointing to the wrong hard disk.
When multiple hard disks are connected it seems,specially when IDE and Sata are mixed,GRUB has another way of naming hdd's as we think it should do.

You have to boot into the live cd and use the terminal.
So if you can provide us with the outcome of ```
sudo fdisk -l {l as in like}
```and your menu.lst we can have a look.

To get to your menu.lst you have to mount your ubuntu partition.
Make a mount point```
sudo mkdir /mnt/rescue
```
Now mount your ubuntu partition which you found with the fdisk command,
```
sudo mount /dev/sd? /mnt/rescue
```

To get to your menu.lst```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

---

### Post by rubikfreak on 2006-12-02
I used the ext3 file system for Ubuntu.

Outcome of sudo fsdisk -l:

```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8669    69633711   83  Linux
/dev/sda2            8670        9039     2972025    f  W95 Ext'd (LBA)
/dev/sda5            8670        9039     2971993+  82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9728    78140128+   7  HPFS/NTFS
```

menu.lst:

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
# kopt=root=UUID=6182aa04-5b5a-4400-bea2-ad1c00a61f88 ro
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
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by bulldog on 2006-12-03
If you take a look at your menu.lst you can see windows and ubuntu are pointing to (hd0),and that can't be,they are on separate hard disk.

So windows will start from GRUB so this must be right.
It implies that GRUB is pointing to the wrong hard disk for your Ubuntu.
Try to make the following changes and take a look if it will boot.
```
title		
Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0) <---
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash  <---make hda1 - sda1
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

If this worked you have to make the changes for recovery and memtest as well!!

---

### Post by rubikfreak on 2006-12-03
It worked! Thank you so much bulldog.

---

### Post by bulldog on 2006-12-03
Naah,just a lucky guess :D 
Have fun with it.

---

