---
title: "GRUB Error 15"
date: 2008-07-10
forum: General Help
---

### Post by axcairns on 2008-07-10
Hey all,

This is doing my head in. One of the drives in my pc died. Luckily it was not the root/boot drive, however, thanks to SATA drives being listed before PATA, it did screw up the ordering of the drives. My root drive was sdc and is now sdb.

I followed the instructions on restoring GRUB (find /boot/grub/stage1, root (hd1,0), setup (hd1)), quit) but I am still getting an Error 15 (file not found).

I have double checked all files and can't see where I am going wrong.

fdisk -ul -

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d73fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23eb23ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    75152069    37576003+  83  Linux
/dev/sdb2        75152070    78156224     1502077+   5  Extended
/dev/sdb5        75152133    78156224     1502046   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcad2cad2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   312576704   156288321   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   625137344   312568641   83  Linux

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   625137344   312568641   83  Linux

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   625137344   312568641   83  Linux

```

cat /boot/grub/device.map

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

```

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
timeout		3

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
# kopt=root=UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic ALLAN
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a18aa44e-85df-4021-b0a8-ce66d12af9c5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
#UUID=3bc36495-dfab-4d5b-ac8c-ee65c933b4e2 /media/mythtv   ext3    relatime        0       2
# /dev/sdd1
#UUID=16753d16-d26a-4656-a02c-7f298cb17777 /media/backup2  ext3    relatime        0       2
# /dev/sdb5
UUID=80a68649-1c45-4c6d-9ae1-e17ad0ba83be none            swap    sw              0       0
# cd-rom
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

ls /boot

```
abi-2.6.24-16-generic     config-2.6.24-18-generic      initrd.img-2.6.24-16-generic.bak  initrd.img-2.6.24-19-generic.bak  System.map-2.6.24-19-generic
abi-2.6.24-18-generic     config-2.6.24-19-generic      initrd.img-2.6.24-18-generic      memtest86+.bin                    vmlinuz-2.6.24-16-generic
abi-2.6.24-19-generic     grub                          initrd.img-2.6.24-18-generic.bak  System.map-2.6.24-16-generic      vmlinuz-2.6.24-18-generic
config-2.6.24-16-generic  initrd.img-2.6.24-16-generic  initrd.img-2.6.24-19-generic      System.map-2.6.24-18-generic      vmlinuz-2.6.24-19-generic

```

Everything I see indicates that hd1 is the drive and hd1,0 the boot partition. I can't think what I have done wrong.

Help!

Allan

---

### Post by VMC on 2008-07-10
Looks like everything is correct.  Your fstab and grub menu match, and since you found grub stage1, I'm not sure.

Did you ty the "sudo blkid" just to make sure they line up?

---

### Post by axcairns on 2008-07-11
Got it working. Instead of ```
setup (hd1)
``` I had to ```
setup (hd0)
``` and set hd0 as the first boot drive in BIOS. 

Bear in mind the /boot/ directory is still on hd1,0 aka sdb1. For some reason GRUB doesn't like my PATA hd1 as the location for it's MBR install but will quite cheerfully work in the SATA hd0's MBR pointing to the /boot/ directory on hd1,0. :confused:

I might still try your suggestion when I got home to see if that sheds any light. 

Thanks,

Allan

---

