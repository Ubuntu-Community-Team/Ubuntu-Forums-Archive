---
title: "mdadm boot problem"
date: 2008-01-24
forum: General Help
---

### Post by Adalgiso on 2008-01-24
Hi,

i searched "all" threads and tried out the solutions i found there, but could, unfortunately, not find a solution for my problem. I managed to get RAID1 running. Whenever i unplug one of the drives and try to boot, the boot process just stops and leaves me with a black screen. Waiting, until i get a console, as some users suggest here, did not help (the system just stops and does nothing, after half an hour i gave up). I put in my /etc/fstab, my /etc/mdadm/mdadm.conf and my /boot/grub/menu.lst, to give you some more insight. In addition, i also post the output of /proc/mdstat

Thankful for every help!

P.S.: Sorry for the smilies in the menu.lst, i don't know how to turn them off.

> root@spaceshuttle:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
#UUID=8b3928a1-ea02-4694-9797-e1c5d3826246 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
#UUID=be647504-22e4-4cf9-8ded-078d93549894 /home           ext3    defaults        0       2
# /dev/sda3
#UUID=1ea8aa11-96e2-4f4d-a24c-396cf1205d39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
###############################################################################
/dev/md0        /       ext3    defaults,noatime                0       1
/dev/md1        /home   ext3    defaults,user,exec              0       2
/dev/md2        none    swap    sw 

> root@spaceshuttle:~# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions

# auto-create devices with Debian standard permissions
#CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
#HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
#MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Tue, 08 Jan 2008 10:51:25 +0100
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $

DEVICE  /dev/sda1 /dev/sda2 /dev/sda3 /dev/sdb1 /dev/sdb2 /dev/sdb3

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=6cc7c9bd:56395ef8:9871736b:ea154d12
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=8439439a:740e55e8:82208710:8da2d0ff
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=fbc4730a:fae2f6bc:bb656c16:8fe50040


> root@spaceshuttle:~# cat /boot/grub/menu.lst 
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
default         0
fallback        1

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
# kopt=root=UUID=8b3928a1-ea02-4694-9797-e1c5d3826246 ro

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro splash
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro splash
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro splash
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8b3928a1-ea02-4694-9797-e1c5d3826246 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



> root@spaceshuttle:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda3[0] sdb3[1]
      2016064 blocks [2/2] [UU]
      
md1 : active raid1 sda2[0] sdb2[1]
      212893312 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      97659008 blocks [2/2] [UU]
      
unused devices: <none>



---

### Post by Adalgiso on 2008-01-26
Really noone with an idea???

Best regards

---

### Post by unlotto on 2008-01-30
I would guess this is happening because grub is installed to the mbr or a partition of the drive you're unplugging.

---

### Post by Adalgiso on 2008-01-31
I installed grub on both drives in order to be able to continue my work or reboot the system in case one drive collapses. I cannot boot, whichever drive i unplug, it only works with both drives.

Best regards

---

### Post by unlotto on 2008-01-31
so grub starts fine and you begin the boot process?

In this case perhaps you should try adding raid1 (and maybe mdadm) to /etc/initramfs-tools/modules and do a dpkg-reconfigure initramfs-tools

I can't find anything wrong with your posted configs. I can only guess what other things you've tried. :)

---

### Post by Adalgiso on 2008-02-02
I'll give it a try. Just one question: So you suggest, the update-initamfs does not work properly? Because i already added raid1 to the initrd.img-file. I'll add mdadm as well, let's see what happens. I'll let you know. Best regards and thank you for trying to help me

---

