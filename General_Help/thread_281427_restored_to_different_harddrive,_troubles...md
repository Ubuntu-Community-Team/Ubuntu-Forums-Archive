---
title: "restored to different harddrive, troubles.."
date: 2006-10-21
forum: General Help
---

### Post by toykilla on 2006-10-21
I backed up my entire system and restored it to a new drive. Mostly it is working but I am having a few troubles. 

The original system was on /dev/sdb2. Now it is restored on /dev/sda2. I can boot just fine, but my storage disk /dev/sdb2 cannot mount. Under System-->Administration-->Disks I see that / is mounted at /dev/sdb2, but this cannot be since it is actually on /dev/sda2, which is mounted as "none"

---

### Post by aysiu on 2006-10-21
By what method did you back up and restore?

Also, can you post the output of these commands? ```
cat /boot/grub/menu.lst
cat /etc/fstab
sudo fdisk -l
df -h
```

---

### Post by toykilla on 2006-10-21
I used tar to backup all of / then restored it. I had to edit grub to boot correctly. 

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout                10

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
# kopt=root=/dev/sdb2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, kernel 2.6.15-23-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-23-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
#title          Microsoft Windows XP Professional
#root           (hd0,0)
#savedefault
#makeactive
#map            (hd0) (hd1)
#map            (hd1) (hd0)
#chainloader    +1

```cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    iocharset=utf8,umask=000 0 0
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdc1       /media/sdc1     vfat    iocharset=utf8,umask=000 0 0
/dev/sdd1       /media/sdd1     vfat    iocharset=utf8,umask=000 0 0
/dev/sdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```sudo fdisk -l
```

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463        8908    35712495   83  Linux
/dev/sda3            8909        9039     1052257+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      581463   293057320+   b  W95 FAT32

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24792   199141708+   c  W95 FAT32 (LBA)

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    b  W95 FAT32
```df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              34G  8.7G   24G  28% /
varrun                503M  172K  503M   1% /var/run
varlock               503M  4.0K  503M   1% /var/lock
udev                  503M  140K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
/dev/sdc1             190G  179G   12G  94% /media/sdc1
/dev/sdd1             466G  185G  281G  40% /tmp/disks-conf-sdd1
```

---

### Post by aysiu on 2006-10-21
I'm sorry but your terminal output indicates that System > Administration > Disks is correct.

/dev/sdb2 is your /

That's what you booted to. That's your main filesystem that you're using. The only thing in there indicating /dev/sda2 is your /boot/grub/menu.lst. Is it possible that the version you're using now isn't the Grub that's installed to the MBR?

How many versions of Ubuntu do you have installed right now?

---

### Post by toykilla on 2006-10-21
Disk manager is showing the partitions on the wrong drives. My operating systems are installed on the 70gig drive, while the 300gig drive has only storage space. 

The first disk has 2 partitions. Windows on partition 1, Ubuntu on partition 2. 

Hard Disk 1
69.25 GiB
Partition 1  ---  /dev/sda1  ---  Windows Virtual FAT (vfat)  ---  /media/sda1  --- 34.18GiB (31.18 GiB Free)
Partition 2  ---  /dev/sda2  ---  Ext 3  ---  none  --- 34.06 GiB (Free space not available)
Swap Partition  ---  /dev/sda3  ---  Memory Swap  ---  1.00GiB (Free space not available)

The second disk only has 1 partition: 300GiB. It shows up fine under Windows, but in Linux I see this:

Hard Disk 2
279.48 GiB
Partition 1  ---  /dev/sdb1  ---  Windows NTFS  ---  /media/sdb1  --- 279.48GiB (Free space not available)
Partition 2  ---  / ---  Ext 3  ---  none  --- ??
Swap Partition  ---  /dev/sdb3  ---  Memory Swap  ---  Free space not available

I cannot access the 300gig drive from Linux.

---

### Post by toykilla on 2006-10-21
edited fstab and it is now working

---

