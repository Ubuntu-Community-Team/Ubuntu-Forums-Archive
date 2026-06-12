---
title: "[SOLVED] Ridiculously slow boot"
date: 2007-06-25
forum: General Help
---

### Post by mahasmb on 2007-06-25
It takes Feisty more than 4 minutes to boot up.

Here's my boot/grub/menu.lst

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
timeout		30

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


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
# kopt=root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST



```

sudo fdisk -l
```
sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3916    31455238+   c  W95 FAT32 (LBA)
/dev/hda2            3917        4014      787185   82  Linux swap / Solaris
/dev/hda3            4015        7296    26362665   83  Linux
maha@maha-laptop:~/.beryl$ 

```

Can someone please help me with this problem?

---

### Post by LaRoza on 2007-06-25
How much RAM do you have?

---

### Post by raja on 2007-06-25
As it starts booting, do Ctr-Alt-F1 to see where the booting process gets stuck too long.

---

### Post by MCSE_Crossover on 2007-06-25
Or what you can try doing is changing your kernel boot parameters from:

boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash

to:

boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro

which is removing the "quiet" and "splash" from the end. Then you will see all the text output and can see where exactly it is taking a long time to get through. Hope that helps. Mine takes a long time because of IRQ issues on my Asus P5W mobo.

---

### Post by mahasmb on 2007-06-25
It gets stuck after the following for 1 min 55 seconds:
```
*Assembling MD array mdarrays...
*Setting up LVM Volume Groups...
*Starting Enterprise Volume Management System...
*Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
```
I typed the above out myself on another computer.

The rest of it I guess is my network/internet setting itself up whereas it doesn't really stop anywhere for more than five seconds but still takes quite a while.

I have 512 MB of RAM. DDR2 I believe. It's a laptop.

---

### Post by mahasmb on 2007-06-25
> **MCSE_Crossover said:**
> Or what you can try doing is changing your kernel boot parameters from:

boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash

to:

boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro

which is removing the "quiet" and "splash" from the end. Then you will see all the text output and can see where exactly it is taking a long time to get through. Hope that helps. Mine takes a long time because of IRQ issues on my Asus P5W mobo.

Umm... you mean where I can see all the code/text as it boots? It's already set like that.

---

### Post by MCSE_Crossover on 2007-06-25
Ok. Good deal...didn't know that.

---

### Post by louistan3 on 2007-06-25
hey...

u could try installing bootchart to see exactly where your boot up slows down...

```
sudo apt-get install bootchart
```

just type that... and reboot...

then check the chart in /var/log/bootchart/

hope this helps.. :)

---

### Post by mahasmb on 2007-06-25
Thanks!

But the picture file created for the chart is huge. Photobucket doesn't allow me to post it at its full size -_-

So I've uploaded it to Yousendit instead... which means anyone who wants to look at it will have to download it. If you can offer any other alternative, I'll go for it if it's free. Otherwise if you don't mind, here's the URL:

[http://download.yousendit.com/FDC3AC3C2E8C70AC](http://download.yousendit.com/FDC3AC3C2E8C70AC)

---

### Post by mahasmb on 2007-06-26
Anyone have any clue how to fix this? I keep searching the forums for a solution but get nothing

---

### Post by raja on 2007-06-26
The boot chart is simply too big and complicated to make any sense of (atleast for me). But seeing your previous post - you suggest that it gets delayed at fschk ? The filesystems should not be checked at every boot usually. Can you post your /et/fstab ?

---

### Post by mahasmb on 2007-06-26
Is this it?

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=8144-5EEF /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=7d453573-3f92-4221-a084-0824702ae520 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by raja on 2007-06-26
In the line for /dev/hda1, the last number should be 2 instead of 1 - as far as I know. If that doesnt make a difference, just change that from 1 to 0 so that that fat partition is not checked. ```
# /dev/hda1 -- converted during upgrade to edgy
UUID=8144-5EEF /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 0
```

---

### Post by mahasmb on 2007-06-26
Raja, THANK YOU!

That really worked. It only takes a little longer than 60 seconds for Ubuntu to boot up.

---

### Post by gigaferz on 2007-06-28
which one did you do , o or 2??

---

### Post by mahasmb on 2007-06-28
I changed it to 0 (zero).

---

### Post by hito1 on 2007-07-07
> **raja said:**
> In the line for /dev/hda1, the last number should be 2 instead of 1 - as far as I know. If that doesnt make a difference, just change that from 1 to 0 so that that fat partition is not checked. ```
# /dev/hda1 -- converted during upgrade to edgy
UUID=8144-5EEF /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 0
```

Would this be valid to every instalation?

My boot is also very slow because ubuntu always fschk my disks.

---

