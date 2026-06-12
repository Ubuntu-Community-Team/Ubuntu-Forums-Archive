---
title: "Grub Error 17, need a little help"
date: 2007-09-16
forum: General Help
---

### Post by mdoyle on 2007-09-16
I have a machine with 3 hard drives, one PATA, the other two are SATA. The first SATA drive has Vista installed on it, the second is used for storage (both are formatted NTFS). At one point I had Ubuntu installed on the second hard drive in it's own partition. I used it to get use to Linux and learn a bit, after breaking it horribly and not wanting to deal with trying to fix it I decided to reinstall, but this time on a new hard drive. So I installed the PATA drive, and installed Ubuntu on there. Before doing that I formatted the old partition and swap that was on hard drive 2.

Now when I turn on my computer I get a Grub Error 17.

I tried reinstalling Grub through the Live CD, it all went like it was suppose to be I am still getting Error 17.

What should I do next to try and get it to boot correctly?

---

### Post by Sef on 2007-09-16
> (GRUB) 17 (error) : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

What did you format your Ubuntu partition.

---

### Post by mdoyle on 2007-09-16
ext3

---

### Post by confused57 on 2007-09-16
Have you tried to set your hard drive order in bios to boot first to your pata drive?

---

### Post by mdoyle on 2007-09-16
Yes, PATA is the first hard drive to boot.

---

### Post by confused57 on 2007-09-16
Boot the Ubuntu live cd, open a terminal, and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

Also, mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Once you mount your root partition, post your /boot/grub/menu.lst and /boot/grub/device.map.

Are you able to boot Vista by changing the boot order of your hard drives?

---

### Post by mdoyle on 2007-09-16
Yeah Vista boots fine as long as I bypass Grub.

Here is the output of that command.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10444    83886080    7  HPFS/NTFS
/dev/sda2           10444       38914   228682752    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156288086    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3769    30274461   83  Linux
/dev/sdc2            3770        4011     1943865   82  Linux swap / Solaris

---

### Post by confused57 on 2007-09-16
> Yeah Vista boots fine as long as I bypass Grub.
Does this mean you select Vista in grub & it boots OK or do you change your hard drive boot order and Vista boots from Vista's IPL on the mbr of your Vista drive?

It "might" help if you can use the link I gave to mount your root partition and post:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

---

### Post by mdoyle on 2007-09-16
Grub never loads, I get Error 17. So me loading Vista is by selecting that hard drive manually, and it using the Vista IPL to start up.

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
# kopt=root=UUID=23eece8e-9327-4289-88ba-f4847e870f37 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu, kernel 2.6.22-9-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=23eece8e-9327-4289-88ba-f4847e870f37 ro quiet splash
initrd		/boot/initrd.img-2.6.22-9-generic
quiet

title		Ubuntu, kernel 2.6.22-9-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-9-generic root=UUID=23eece8e-9327-4289-88ba-f4847e870f37 ro single
initrd		/boot/initrd.img-2.6.22-9-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

---

### Post by confused57 on 2007-09-16
Since you're not getting the grub boot menu with grub error 17, maybe the solution in this thread will help:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

If you're able to get a grub menu after trying the above "fix", I believe you'll need to change your root from (hd2,0) to (hd0,0) in order to boot Ubuntu.

Added:  Since you're able to boot into Vista, you might want to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's a small download(5-7 Mb) and it may be able to boot Ubuntu...it's an excellent utility to have, whenever you have booting problems.

---

### Post by mdoyle on 2007-09-16
Not sure if every mobo is suppose to have those options, but mine doesn't. Downloading Super Grub now.

---

### Post by confused57 on 2007-09-16
Give SGD a try, hopefully it'll boot Ubuntu...if it doesn't, there's one more thing I'd suggest that you try.

Reinstall grub to the mbr of your pata drive, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Use the above link, but it'll be something like:
```
sudo grub
find /boot/grub/stage1
root (hd2,0)
setup (hd2)
quit
```

IF you happen to get a grub boot menu, highlight your Ubuntu entry, press "e", highlight root, press "e" again, change root from (hd2,0) to (hd0,0), press "enter', then "b" to boot...this change is only temporary, if it works it can be made permanent.

---

### Post by mdoyle on 2007-09-16
Not sure why, but the Super Grub disk I made wouldn't boot.

I'll try reinstalling Grub now.

---

### Post by mdoyle on 2007-09-16
find /boot/grub/stage1

Error 15: File not found

Edit: Nevermind on that one. I mistyped stage1 in the terminal. I'm rebooting now with it reinstalled.

---

### Post by mdoyle on 2007-09-16
Ok. Now this is weird. No Grub at all. No errors, no menu, just boots directly to Vista. Yes the PATA drive is still the first to boot. If I go to the Boot Menu and select the PATA drive manually it still boots directly to Vista.

---

### Post by mdoyle on 2007-09-16
Here is another interesting thing. If I unplugged my two SATA drives and try to boot directly to the PATA drive I get a No bootable device error from the mobo.

---

