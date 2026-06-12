---
title: "[SOLVED] Grub messed up after deleting partition"
date: 2008-06-25
forum: General Help
---

### Post by MrMatt2532 on 2008-06-25
I went through this process below after deleting a partition which caused grub to stop working correctly.

sudo grub
find /boot/grub/stage1
root (hd0,5)
setup (hd0)
quit

And yes, for the root and setup steps I used the result from the find step.

Anyways, this did not fix my broken grub. My Ubuntu entry still tries to boot from the wrong partition, and I have to manually edit the entry in order for it to boot up correctly.

Does anybody know what could be wrong and anything else I could try? Thank you.

---

### Post by Zorael on 2008-06-25
That procedure is merely to reinstall grub into the master boot record, to make it *start* grub at all. If your problem is that the grub menu entries are off, do this in a terminal to make it regenerate them.
```
$ sudo update-grub
```

---

### Post by MrMatt2532 on 2008-06-25
That did not fix it, but it gave some information that may help us. Here are the results when I used that command:

Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=14642510-3f40-4dac-a8f2-23aa921ed893'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by MrMatt2532 on 2008-06-25
bump bump

---

### Post by VMC on 2008-06-25
What's the output of this:

```
cat /boot/grub/menu.lst
sudo fdisk -l
sudo blkid
```

---

### Post by MrMatt2532 on 2008-06-25
Results below:

cat /boot/grub/menu.lst
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
# kopt=root=UUID=8c0c282b-3746-4f82-8045-9314e7644f58 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8c0c282b-3746-4f82-8045-9314e7644f58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8c0c282b-3746-4f82-8045-9314e7644f58 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8c0c282b-3746-4f82-8045-9314e7644f58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8c0c282b-3746-4f82-8045-9314e7644f58 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8c0c282b-3746-4f82-8045-9314e7644f58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8c0c282b-3746-4f82-8045-9314e7644f58 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint, kernel 2.6.24-16-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda5 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint, kernel memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

sudo fdisk -l
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009e8fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2771    22258026    7  HPFS/NTFS
/dev/sda2            2772        5990    25856617+   5  Extended
/dev/sda3            5991        7296    10490445    c  W95 FAT32 (LBA)
/dev/sda5            5852        5990     1116486   82  Linux swap / Solaris
/dev/sda6            2772        5851    24740037   83  Linux

Partition table entries are not in disk order
```

sudo blkid
```
/dev/sda1: UUID="EE38B22A38B1F1A7" TYPE="ntfs" 
/dev/sda3: LABEL="STORAGE" UUID="4672-1452" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="2d815d3a-dc15-4e85-8aa2-873e7d288c89" 
/dev/sda6: UUID="8c0c282b-3746-4f82-8045-9314e7644f58" TYPE="ext3"
```

---

### Post by VMC on 2008-06-25
Change this in your menu.lst "root (hd0,6)", to "root (hd0,4)" in all occurrences.

Edit:forget that. I see you have Mint on 0,4. ubuntu is not there. only one linux partition.
You menu.lst reflects ubuntu, but its nowhere to be found. Did you delete somehow.

---

### Post by drs305 on 2008-06-25
It appears all the entries should be reduced by 1 (i.e. hd0,5) for each root entry in the main menu and also in the line # groot=(hd0,6). Make a backup and then change all (hd0,6) to (hd0,5)

However, you probably have another problem. Your fstab probably has an incorrect UUID reference since your repartition. Look at your fstab and see if the UUID info from the 'blkid' command is the same. If it isn't, replace whatever is in fstab with the UUID's from 'blkid'.

**Added**:  I didn't see the Mint reference either. Are you trying to use mint or ubuntu.  Guess I never look much past ubuntu ... ;-)

---

### Post by MrMatt2532 on 2008-06-25
OK, I fixed the Ubuntu entry in fstab by comparing with blkid. Then I fixed menu.lst by changing the hd0,6 entries to hd0,5. While I was at it I deleted the mint entries. This all happened when I deleted the mint partition. Then, I re-ran the update-grub command so that the grub file could be rebuilt. This probably didn't actually do anything, but it just made it so Ubuntu doesn't think i edited it for the future when new kernel entries are installed.

Everything is working correctly now. Thanks guys.

---

