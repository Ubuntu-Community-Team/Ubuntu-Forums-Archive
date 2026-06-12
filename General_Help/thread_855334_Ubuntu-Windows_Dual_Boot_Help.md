---
title: "Ubuntu-Windows Dual Boot Help"
date: 2008-07-10
forum: General Help
---

### Post by darkhorse186 on 2008-07-10
Hi,
I am running ubuntu 8.04 and I would like to set up a dual boot using a separate hard drive. The only thing is most of the guides on the internet explain what to do with windows already installed. Is it just the same or do I have To do things differently?
Thanks
Darkhorse

---

### Post by Elfy on 2008-07-10
Slightly - :)

Once you have installed windows it will remove grub so you will need to reinstall it, you can use your buntu livecd to do that - really easy (usually :D )
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by overdrank on 2008-07-10
> **darkhorse186 said:**
> Hi,
I am running ubuntu 8.04 and I would like to set up a dual boot using a separate hard drive. The only thing is most of the guides on the internet explain what to do with windows already installed. Is it just the same or do I have To do things differently?
Thanks
Darkhorse

Hi and it is preferred to install ubuntu after window but if you choose to do the other way then this link will help
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Dang to slow again lol

---

### Post by darkhorse186 on 2008-07-10
I now have the separate hard drive with windows on it but I have ubuntu set to boot first. I checked the grub menu and it all seems to still be there. What do I do to make grub recognize the installation of windows?

---

### Post by Elfy on 2008-07-10
Can you post the results of these please

```
cat /boot/grub/menu.lst
sudo fdisk -l
```

You have to add it in to the end of the menu file

---

### Post by darkhorse186 on 2008-07-10
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
# kopt=root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro

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

title		Ubuntu 8.04, kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-18-rt

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-17-rt

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f62cf75-ca39-4b1a-95ff-d9754c34bb1f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe417e417

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000efc2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24415   196113456   83  Linux
/dev/sdb2           24416       24792     3028252+   5  Extended
/dev/sdb5           24416       24792     3028221   82  Linux swap / Solaris
```

Also HDD 1 is ubuntu and HDD 0 is Windows

---

### Post by Elfy on 2008-07-10
Sorry 2 more thing to check - at the moment grub says it's booting win when you select a buntu line :)

```
cat /boot/grub/device.map
df /boot
```

---

### Post by darkhorse186 on 2008-07-10
```
(hd0)	/dev/hda
```
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            193034844  22253244 160975928  13% /
```

Ubuntu is HDD 1 in the BIOS though

---

### Post by Elfy on 2008-07-10
Ok - I'm not too sure here, did you add a drive here and connect it to 0 thus moving the buntu drive onto 1?

I think you will need to add the new drive to your device map before menu.lst will boot it, then edit the menu - it is going to look odd though as hd0 should be the win drive :)

Start by backing up the 2 files we will change

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.100708
sudo cp /boot/grub/device.map /boot/grub/device.map.100708
```

Open the device map to edit

```
gksudo gedit /boot/grub/device.map
```

add this line to the end

> (hd1)	/dev/sdasave and quit

Open menu list to edit

```
gksudo gedit /boot/grub/menu.lst
```

add these lines to the end

 > title		Windows 
 root		(hd1,0)
 makeactive
 chainloader	+1 save and exit.

Update grub - if you get any messages - here - post them

```
sudo update-grub
```

Reboot and see if the  change is ok.

But - I'm not totally sure - I would expect someone else to look - I'd wait for a second opinion.

---

