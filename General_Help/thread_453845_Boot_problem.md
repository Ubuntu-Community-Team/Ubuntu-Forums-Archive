---
title: "Boot problem"
date: 2007-05-24
forum: General Help
---

### Post by guernicaaa on 2007-05-24
Another problem arose today in my adventure into Ubuntu.  I installed Ubuntu on a 50GB partition on a fresh 300GB hard drive.  After a couple days, I needed to use Windows to do some things, so I decided to re-install on the rest of the 300GB hard drive (my installation on my other drive was f***ed)
The install went alright, booted into Windows, and after installing a few drivers, I needed to reboot, so I did.  But then my PC started using the NVIDIA Boot Agent, instead of GRUB.  And when I boot up, I get this:
NVIDIA Boot Agent 201.0440
some copyright info...
my MAC address it looks like?
then it says:
PXE-E53: No boot file name received

PXE-M0F: Exiting NVIDIA Boot Agent.
DISK BOOT FAILURE, ENTER SYSTEM DISK AND PRESS ENTER

How can I change my boot loader to GRUB instead of this garbage NVIDIA one?  Can I use a live CD (like the one I installed Ubuntu from) and change this?

---

### Post by psusi on 2007-05-24
Is your bios set to boot from the hard disk?  It looks like it either isn't set to boot from a hard disk, or can't find one that looks bootable, so it is trying to boot from the network.

---

### Post by guernicaaa on 2007-05-26
Okay I fixed this problem by using the Ubuntu Live CD and restoring Gnome, but I got a problem, Windows doesn't show up in the boot list.  I've looked at thread on how to add Windows to this list, but I don't know the partiition number on it.  ie: hd(0,?)
I dunno which partition it's on.  I've tried 0, 1, and 2 in my /boot/grub/menu.lst and none of them work.  They all say Partition not found or something.  How can I find out which partition number Windows is on?

---

### Post by confused57 on 2007-05-26
> **guernicaaa said:**
> Okay I fixed this problem by using the Ubuntu Live CD and restoring Gnome, but I got a problem, Windows doesn't show up in the boot list.  I've looked at thread on how to add Windows to this list, but I don't know the partiition number on it.  ie: hd(0,?)
I dunno which partition it's on.  I've tried 0, 1, and 2 in my /boot/grub/menu.lst and none of them work.  They all say Partition not found or something.  How can I find out which partition number Windows is on?

Open a terminal and run the command:
```
sudo fdisk -l
```
the -l is a lowercase "L"

hda4 = (hd0,3)
hda5 = (hd0,4)
hda6 = (hd0,5)

your partitions may be designated sda, instead of hda.

---

### Post by guernicaaa on 2007-05-27
okay it says sda2, so I tried hd(0,2) and it said partition not found.   in my menu.lst it says that ubuntu is hd(0,0).  I know for one of the many configurations I've tried, it said NTDLR missing or something, so does that mean it actually found windows?  if so, how can I fix that error?  does the windows installation have to be on a primary partition, because I'm not sure if it is or not.  I formatted my harddrive with gparted and installed ubuntu, then had the windows installation create another partition for its installation.  how can I get it to boot both?  or should I just reformat the whole hard drive and install windows first, then ubuntu (I hope I don't have to resort to this)
thanks for your help guys

---

### Post by psusi on 2007-05-28
What was the output of sudo fdisk -l?  And is this one hard disk, or do you have two?

---

### Post by guernicaaa on 2007-05-29
```

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   83  Linux
/dev/sda2   *        6080       36480   244196032+   7  HPFS/NTFS

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        6374    51199123+   7  HPFS/NTFS
/dev/hdd2   *        6375       12748    51199155    7  HPFS/NTFS
/dev/hdd3           12749       24321    92960122+   7  HPFS/NTFS

```
and don't mind the second hard drive that shows up in my fdisk output, that's just media (movies,music,etc)
i;m just trying to get the one drive to boot ubuntu and windows.

---

### Post by confused57 on 2007-05-29
You might also want to post the output of:
```
gedit /boot/grub/menu.lst
```
you can just post the entries to boot Ubuntu

---

### Post by guernicaaa on 2007-05-29
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
# kopt=root=UUID=5b6c831c-93ca-4471-b285-6fdb31cf7f11 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5b6c831c-93ca-4471-b285-6fdb31cf7f11 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5b6c831c-93ca-4471-b285-6fdb31cf7f11 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5b6c831c-93ca-4471-b285-6fdb31cf7f11 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5b6c831c-93ca-4471-b285-6fdb31cf7f11 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
when I use this config, I get "Partition not found" error.

---

### Post by confused57 on 2007-05-29
If your Ubuntu boots OK with the menu.lst you posted, then an entry similar to this might boot Windows:

```
title     Windows XP
rootnoverify  (hd0,1)
savedefault
makeactive
chainloader +1
```

I'm assuming you mean Windows will not boot when you say "when I use this config, I get "Partition not found" error"...

Sometimes it can be difficult to boot Windows when it is located on a partition after the Ubuntu partition.

Added:  To edit your menu.lst:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
add the Window's entry to the very end of the menu.lst file

---

### Post by guernicaaa on 2007-05-30
When I add that to my menu.lst, I get an NTLDR is missing error and windows won't boot.  :\

---

### Post by psusi on 2007-05-30
Is windows installed on the 200 gig or the 300 gig drive?

---

### Post by guernicaaa on 2007-05-30
the 300.  I formatted the whole 300 gig drive.  Then installed Ubuntu on a 50 gig partition that I created using the live CD.  Then I installed Windows on the rest of the hard drive (250 gig partition created using the windows installer).

---

### Post by guernicaaa on 2007-06-03
bump
anybody?  i'd love to get into windows to do a few things...

---

### Post by confused57 on 2007-06-03
> **guernicaaa said:**
> bump
anybody?  i'd love to get into windows to do a few things...
You might want to try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it might be able to boot your Windows

Also, in Ubuntu, open a terminal & post the output of:
```
gedit /boot/grub/device.map
```

---

### Post by coolzgeek on 2007-06-03
> **confused57 said:**
> If your Ubuntu boots OK with the menu.lst you posted, then an entry similar to this might boot Windows:

```
title     Windows XP
rootnoverify  (hd0,1)
savedefault
makeactive
chainloader +1
```

I'm assuming you mean Windows will not boot when you say "when I use this config, I get "Partition not found" error"...

Sometimes it can be difficult to boot Windows when it is located on a partition after the Ubuntu partition.

Added:  To edit your menu.lst:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
add the Window's entry to the very end of the menu.lst file

Confused is right. Or if this method doesn't work, get the alternate install disk install by text mode and see whether setup says it detects Windows

---

### Post by adrian15 on 2007-06-03
Can you please try:

Super Grub Disk -> Windows -> Boot Linux from 2nd hard disk

I think that the windows installation has copied some boot files to the hdd hard disk, as long as in hdd there's a windows first partition and in sda there's no first partition.

If it boots, tell people how to use the map commands in order to edit your menu.lst.

adrian15

---

### Post by guernicaaa on 2007-06-03
[quote=device.map](hd0)	/dev/sda[/quote]
i'll try the super grub disk right now and report back

EDIT:
ALRIGHT!  Windows booted perfectly with that super grub disk.  Now, do I have to do that every time?  All I did was boot into the super grub disk and choose Boot Into Windows.

---

### Post by confused57 on 2007-06-03
adrian15 will probably be able to help you get Window's booted from grub, but you might want to try this Window's entry:
```
title      Windows XP
unhide     (hd0,1)
hide       (hd0,0)
root       (hd0,1)
savedefault
makeactive
chainloader +1
```

This method works to hide other Windows OSes, but don't know if it'll work with hiding Linux:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
scroll down in the link to find the explanation for this

---

