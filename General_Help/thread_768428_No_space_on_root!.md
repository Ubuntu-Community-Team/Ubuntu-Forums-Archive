---
title: "No space on root!"
date: 2008-04-26
forum: General Help
---

### Post by chrisN_uk on 2008-04-26
Erm, during an upgrade to hardy, my root partition seems to have filled itself up, causing the installation to be incomplete (First time I rebooted, I was told I have read only root. Not pretty but I'm impressed with how resilient linux is, it seems to have fixed itself and despite the installation going wrong, I am using hardy to type this now although several arts of the system aren't working.) 

I have created a new partition and copied the contents of / over, but how do I now set things to boot from this new partition and mount it as / ? I've tried editing /etc/fstab and /boot/grub/menus.lst but they don't give nice results.

Thanks, 
Chris

---

### Post by chrisccoulson on 2008-04-26
Can you post the contents of /etc/fstab and /boot/grub/menu.lst please? Could you also post the outputs of the following 2 commands:
```
sudo blkid
sudo fdisk -l
```

---

### Post by chrisN_uk on 2008-04-26
$ sudo blkid
/dev/sda2: UUID="10e505b0-4c53-4d5b-82d3-4530cb9d1ed5" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="d4f48201-7424-4644-a84f-dbf1ddcf5694" 
/dev/sda4: UUID="00e0046e-0ac8-484c-b11c-db251532b090" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="10e505b0-4c53-4d5b-82d3-4530cb9d1ed5" SEC_TYPE="ext2" TYPE="ext3" 

$ sudo fdisk -l

Disk /dev/sda: 81 GB, 81956689920 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1        2357    18932571   83  Linux
/dev/sda2   *        4973        6241    10185210   83  Linux
/dev/sda4            6242        9657    27430987   83  Linux
/dev/sda3            9658        9964     2457945   82  Linux swap

No idea how sda1 and sda2 can have the same uuid! I used gparted to copy sda2...It certainly was different a when I first did this. Here are fstab and menu.lst (unedited, they allow me to load ubuntu)

/etc/fstab
```

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda4 :
UUID=00e0046e-0ac8-484c-b11c-db251532b090 /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=8C60341C60340F86 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda3 :
UUID=d4f48201-7424-4644-a84f-dbf1ddcf5694 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


/dev/sda1  /mnt/hda1      ext3      user 0 0

```

/boot/grub/menu.lst

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
timeout		5

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
# kopt=root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash rootflags=data=writeback

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
# altoptions=(recovery mode) single rootflags=data=writeback

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.22-9-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.22-9-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=10e505b0-4c53-4d5b-82d3-4530cb9d1ed5 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by chrisccoulson on 2008-04-27
If you copied an image of a partition, then you'll end up with the same UUID. I'm not sure how GParted handles the copying of partitions. 

Did you copy from sda2 to sda1? If so, in your case it should just be a case of changing the UUID on the old partition and modifying the groot option in your menu.lst:
```
sudo tune2fs -U random /dev/sda2
```
...should give /dev/sda2 a new random UUID.

You will also need to change the following line in your menu.lst:
```
# groot=(hd0,1)
```
...to...
```
# groot=(hd0,0)
```
...and then run... 
```
sudo update-grub
```
Make sure that all the following lines in your menu.lst:
```
root		(hd0,1)
```
...now look like this:
```
root		(hd0,0)
```

---

### Post by chrisN_uk on 2008-04-27
Thanks, that worked like a charm!

And yes, I did just copy it from sda2. 

Chris

---

