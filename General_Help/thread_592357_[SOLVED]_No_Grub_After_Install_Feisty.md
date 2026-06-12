---
title: "[SOLVED] No Grub After Install Feisty"
date: 2007-10-26
forum: General Help
---

### Post by rolodoom on 2007-10-26
I have 2 SATA drives with the next partitions on it: sda1(system), sda3(home), sda5(swap) sdb1(work,data).

The problem is:

I reinstall ubuntu feisty amd 64. I follow all instructions from liveCD, and format sda1 (delete partition, create a new one, format to ext3), and format swap partition.

Everything worked fine and finished the setup.

Then I was asked to reboot, and then surprise: Cannot boot into my ubuntu, the only way to boot is putting the liveCD on the drive, and choosing to boot from first hard disk on the liveCD initial menu.

How can I fix this to boot from the hard drive?  I have searched on the forum but none of the solutions has worked for me. Maybe I'm missing something, so any help would be appreciated.

Only have ubuntu installed.


Here is a copy of my menu.lst and my fstab:

MENU.LST
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
# kopt=root=UUID=5559d956-10f4-4c76-99e5-7e393e84106b ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5559d956-10f4-4c76-99e5-7e393e84106b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5559d956-10f4-4c76-99e5-7e393e84106b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

FSTAB:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5559d956-10f4-4c76-99e5-7e393e84106b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=4b74edb3-4172-4da5-ab93-2ff378ac43d8 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=20c8b0a4-4cdf-4c71-a233-b911f46d9ecf /media/sdb1     ext3    defaults        0       2
# /dev/sda5
UUID=191978bf-6e51-488e-b5b4-916a705cb47a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by jusmurph on 2007-10-26
Make sure in your bios, that the Hardrive the Ubuntu partition is on, is first in the boot order.

---

### Post by rolodoom on 2007-10-26
> **jusmurph said:**
> Make sure in your bios, that the Hardrive the Ubuntu partition is on, is first in the boot order.

I had already checked that. Ubuntu partition is on, and read at first by BIOS.

---

### Post by meierfra on 2007-10-26
Menu.lst and fstab look  fine. So we need more information. 

Do you get any error messages during  boot up?
If you press "esc" during boot up, does the grub menu appear?
Post the output of:
```
sudo fdisk -l
```
and 
```
 cat /boot/grub/device.map
```

---

### Post by rolodoom on 2007-10-27
I fixed the problem, not the way I like it, but the way I could do it.

First I tried re-installing the system, but can't boot after, again needed to use livecd to boot. So, I figured out the problem was something about the partition (what?, don't know).

So decided to make full data backup from sda2, then delete all partitions from sda and reinstall system.

Then, system is OK and running, and booting.

Thanks, for the replies.

---

