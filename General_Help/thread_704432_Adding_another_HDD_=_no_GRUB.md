---
title: "Adding another HDD = no GRUB"
date: 2008-02-22
forum: General Help
---

### Post by tirux on 2008-02-22
I can't figure this out. Whenever I add another HDD as slave my GRUB simply disappears. This problem might be because I had Ubuntu 7.10 installed on both hard drives, but even after I completely formatted the second HDD, it is causing me trouble.

So right now I disconnected my second HDD to get in Ubuntu. I check that I have /dev/sda1 to boot, my device.map says I only have "(hd0)   /dev/sda", and here is my menu.lst:

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
# kopt=root=UUID=2570c4fa-0585-444a-8e8a-501347ab139c ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2570c4fa-0585-444a-8e8a-501347ab139c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2570c4fa-0585-444a-8e8a-501347ab139c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Can someone help me figure this out? I can use LiveCD when I add my second HDD and also check what might be the problem, but seriously I don't know what it is!

---

### Post by torgrot on 2008-02-22
Are these SATA or IDE drives?  Do both drives show up in the BIOS set up screen?  What is the boot order in BIOS?

torgrot

---

### Post by tirux on 2008-02-22
> **torgrot said:**
> Are these SATA or IDE drives?  Do both drives show up in the BIOS set up screen?  What is the boot order in BIOS?

torgrot

Both are IDE drives. They both show in the BIOS, and I have correctly set up which is master and which is slave with the jumpers and in the boot order.

---

### Post by torgrot on 2008-02-22
On the IDE cable are there three different color connectors?  If so that is a cable select cable.  You would need to jumper them all as cable select.  The drive at the end of the cable is then the master and the drive in the middle is the slave.  Don't assume, make sure.  I have fought many problems with this when a second drive is connected.

torgrot

---

### Post by tirux on 2008-02-22
> **torgrot said:**
> On the IDE cable are there three different color connectors?  If so that is a cable select cable.  You would need to jumper them all as cable select.  The drive at the end of the cable is then the master and the drive in the middle is the slave.  Don't assume, make sure.  I have fought many problems with this when a second drive is connected.

torgrot

Yes I remember the black end of the IDE cable is the master and the grey is the slave. I am going to try that once I get back home.

---

### Post by dstew on 2008-02-22
> Whenever I add another HDD as slave my GRUB simply disappears.You mean you do not get even the grub menu? Do you get any error message?

If you get no error message, or just a BIOS error, then the grub stage1 is not being loaded. That means that the boot disk order has been changed by the addition of a disk. If you get a "grub loading" message, then an error with no explanation, that is a stage1.5 error. That means that the correct disk booted, but grub could not find its menu. That is because the location of the partition that contains the menu (and grub stage2) is written into the stage1.5 at installation. Stage1.5 can find the file as long as it points to the correct partition. But if the disks change, it might not be able to find its partition.

---

