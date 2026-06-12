---
title: "cannot access windows through grub menu"
date: 2008-01-19
forum: General Help
---

### Post by tbuss on 2008-01-19
I have three hdd's (2 internal and 1 external) 

/dev/sda1 ntfs
/dev/sdb1 ext3 /
/dev/sdb2 ext3 swap
/dev/sdc1 ext3 external drive

I installed Ubuntu on my 2nd internal hdd leaving the 1st hdd unpartitioned.
I mounted my external drive as ext3, mounted on /media/disk
Everything worked as advertised. I then decided to dual boot with windows.
I installed windows xp pro on my first internal hdd /dev/sda1 
After installation I was unable to boot into Linux.
I then reinstalled grub on /dev/sdb1 (using install disc)
After reinstalling grub I edited the grub menu list:

**sudo gedit /boot/grub/menu.list**

```
Uncommented the example for windows in menu.lst and added to the boot order
title windows xo professional
root (hd0,0)
makeactive
chainloader +1
```

When I enter the grub menu after a sys restart I select windows xp pro from the list, the grub menu restarts the timeout until I hit esc; windows never loads.
I'm then presented with a list again, I select Ubuntu 7.10 and linux boots with no problems.
What do I need to do so that I can boot into windows?

---

### Post by logos34 on 2008-01-19
If you're booting from sda, then the above windows entry (hd0,0) should work.  But if you're booting from sdb, then you'll need an [entry like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands").

You might want to post your full menu.lst and /boot/grub/device.map.  Also,

**sudo fdisk -l**

---

### Post by tbuss on 2008-01-19
logos34, here is my menu.lst /boot/grub/device.map and results for sudo fdisk-l

**sudo fdisk -l**

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x027ab630

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14759   118551636   83  Linux
/dev/sdb2           14760       14946     1502077+   5  Extended
/dev/sdb5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57b4fd21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36483   293049666   83  Linux
```

**menu.lst**

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
# kopt=root=UUID=7c6cc71a-db3f-4300-8800-07bbc0a35e5d ro

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

title		Windows XP Professional
rootnoverify		(hd0,0)
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6cc71a-db3f-4300-8800-07bbc0a35e5d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6cc71a-db3f-4300-8800-07bbc0a35e5d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

**/boot/grub/device.map**

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

---

### Post by logos34 on 2008-01-19
My guess is something's wrong on the windows side.  You're booting to grub on sda, and the entries all look correct.  Grub can't chainload XP at (hd0,0) for some reason.  

You could try booting into the recovery console on the xp install cd (press 'R') and at the prompt run

**fixboot**

and then

**chkdsk /r**

Maybe one or both will fix whatever the problem is.  

Note: Don't leave XP boot entry inside the 'automagic' section in menu.lst.  Put it below the line 
> ### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by tbuss on 2008-01-19
logos34,

I did as you said,

> You could try booting into the recovery console on the xp install cd (press 'R') and at the prompt run

fixboot

and then

chkdsk /r

Maybe one or both will fix whatever the problem is.

After a restart my box booted directly into windows. Do I need to reinstall GRUB?

---

### Post by logos34 on 2008-01-19
> **tbuss said:**
> logos34,

I did as you said...

After a restart my box booted directly into windows. Do I need to reinstall GRUB?

Sounds like you ran fixmbr. (at least we know windows is fine. now)

Yep, reinstall grub.

---

### Post by logos34 on 2008-01-19
wait...why not boot linux from windows?  might as well try--not having much luck with grub.

Get Wingrub.  [Read this.]("http://users.bigpond.net.au/hermanzone/p9.html")  Seems more involved that it really is.  But if you follow Herman's instructions it should work.

---

