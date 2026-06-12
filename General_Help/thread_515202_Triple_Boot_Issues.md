---
title: "Triple Boot Issues"
date: 2007-08-01
forum: General Help
---

### Post by DeclanMcErlane on 2007-08-01
Hey I'm a new member here but I've been using Ubuntu every often to try and get used to the OS.

My initial setup was a dual-boot with XP and Ubuntu, both working fine and dandy, but I wanted to see what Vista was like so I tried to install it as a seperate boot. In order to do this, first I needed to create a new partition.

I used Partition Manager for Windows to create free space for Vista but later realised I couldn't create another partition because I already had four on the one hard-drive. They are listed below...

1) FAT32 - 5GB or so (don't know what this was for)
2) NTFS - 112GB (for XP)
3) Unallocatedd Space - 16GB for Vista
4) EXT3 - 19GB Ubuntu
5) Extened Swap - 1GB for Ubuntu as well

From there I tried to use GParted to create the partition but still no luck, so I decided to delete the FAT32 partition leaving me with two regions of unallocated space

1) Unallocated Space
2) NTFS - 112GB (for XP)
3) Unallocatedd Space - 16GB for Vista
4) EXT3 - 19GB Ubuntu
5) Extened Swap - 1GB for Ubuntu as well

From there I then formatted parition 3 to NTFS for Vista. I proceeded to install Vista and many reboots later it was finally installed, new and shiny out of the box, leaving my hard-drive partitoned as so...

1) Unallocated Space
2) NTFS - 112GB (for XP)
3) NTFS - 16GB for Vista
4) EXT3 - 19GB Ubuntu
5) Extened Swap - 1GB for Ubuntu as well

 I then realised that grub had been replaced by the Vista bootloader but this wasn't too much of an issue as all I had to do was reinstall GRUB.

So, I re-setup GRUB and was able to access both Vista and Ubuntu but to my surprise was not able to access XP. Now looking back to the FAT32 partition I deleted earlier I was wondering whether it would have been purposely put there in order to boot XP.

I tried many a thing to try and get XP to boot again including changing the boot.ini located in my XP partition (C:\) but with no avail.

Now, today I installed Partition Manager on to Vista to try and resize the XP partition as I read on the Microsoft website that this could cause problems for the boot process of XP. Now, i can't even access XP OR Vista. I also cannot access my XP partition with all my documents, which I was able to before, through Ubuntu.

Please someone help me. I am severely stuck and it has been the worst start to a birthday ever!

Many Thanks,

Declan.

---

### Post by meierfra on 2007-08-01
could you post the output of

```
sudo fdisk -l
```

and 

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by distroman on 2007-08-01
I agree post the out put of the commands above.

I have never set xp and vista up on the same system just remember reading about vista causing trouble in that kind of setup might not be an issue anymore.

If I was confident grub was configured correctly I would try to fix xp with either “fixmbr” or “fixboot” if that did any good I would setup grub again.

---

### Post by DeclanMcErlane on 2007-08-02
Here are the outputs

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       15168       17333    17398395    7  HPFS/NTFS
/dev/sda2               1       14458   116133853+   7  HPFS/NTFS
/dev/sda3           17334       19906    20667622+  83  Linux
/dev/sda4           19907       20023      939802+   f  W95 Ext'd (LBA)
/dev/sda5           19907       20023      939771   82  Linux swap / Solaris

```

and...

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
default		7

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
# kopt=root=UUID=16655d2b-aa54-42f4-be0d-3a3328c3f73e ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=16655d2b-aa54-42f4-be0d-3a3328c3f73e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=16655d2b-aa54-42f4-be0d-3a3328c3f73e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16655d2b-aa54-42f4-be0d-3a3328c3f73e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16655d2b-aa54-42f4-be0d-3a3328c3f73e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

I am also unable to perform fsck /dev/sda2 and /dev/sda2 wil not mount properly so I cannot access my files through Ubuntu. I even tried mount -f /dev/sda2 and still no luck. Thanks. Declan.

---

### Post by meierfra on 2007-08-02
I looked at your  fdisk  and menu.lst a couple of times today and never saw anything wrong. Finally I noticed something odd in your fdisk:  Your windows xp partition (sda2) is not  marked as bootable. 

Linux partition don't need the  "boot flag" to boot. But windows partitions do. Maybe you can just use partition magic or gparted to set the boot flag, but I'm not sure.

---

### Post by DeclanMcErlane on 2007-08-03
Okay thanks very much but things went for the very worse last night. I tried using Partition Manager to get rid of the unallocated space which hasn't turned out the way I wanted as now neither XP nor Vista are bootable. Therefore I decided to delete my Vista partition. I used GParted to change the boot flag and realised that yes you were right. My XP partition did not have a boot flag. I have so modified it so that it does now. But I'll post sudo fdisk -l again because it has changed to /dev/sda1...

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14458   116133853+   7  HPFS/NTFS
/dev/sda2           14459       17333    23093437+   7  HPFS/NTFS
/dev/sda3           17334       19906    20667622+  83  Linux
/dev/sda4           19907       20023      939802+   f  W95 Ext'd (LBA)
/dev/sda5           19907       20023      939771   82  Linux swap / Solaris

```

I'm going to try and see if Windows will boot and will post back with the results soon. EDIT: Windows still doesn't boot. Should I reconfigure grub. May I also mention that while I was on Windows Vista I tried changing the boot.ini to see if that would make Windows in case that may be what is causing Windows not to boot.

EDIT...again: YES! I deleted the Vista partition and realised that I no longe needed an administrator password to get to recovery console so I fired up the XP OS disk and hit "chkdsk /P /R". It took a long time to finish but it was worth it because I can finally access my documents through Ubuntu. Now I'm going to try and change the boot.ini in my XP partition to see if it will finally boot.

Declan.

---

