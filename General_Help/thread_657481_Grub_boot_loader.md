---
title: "Grub boot loader"
date: 2008-01-03
forum: General Help
---

### Post by wildteen88 on 2008-01-03
I have two 250GB sata HDDs They are laid out as follows:
HDD1 has no partitions and has Windows XP Home Edition installed on (takes up whole drive)

HDD2 has two partitions. The first partition has Windows Vista Home Premium installed (partition ~220GB) and the other partition has Ubuntu installed (partition 20GB (+ 5GB swap partition)).

XP was installed first, followed by Vista. When Vista was installed it added its own bootloader allowing me to boot into either XP or Vista. Ubuntu was installed last and installed GRUB bootloader

I am able to boot successfully in to all OSes through Grub, However in order for me to boot into XP/Vista I have to first select Windows Vista/Longhorn Loader from the GRUB bootmenu this will then load the Vista Bootloader allowing me to boot either XP or Vista

I was hoping weather it'll be possible to add XP and Vista to GRUB so I can bypass the Vista bootloader. Is this possible at all? Or am I better of Adding Ubunut to Vista's bootloader by using EasyBCD and removing GRUB?
Thanks for any help

---

### Post by torgrot on 2008-01-03
No personal experience with it but I think from what I've read that EasyBCD is the way to got with Vista in the mix.

torgrot

---

### Post by LaRoza on 2008-01-03
> **wildteen88 said:**
> I have two 250GB sata HDDs They are laid out as follows:
HDD1 has no partitions and has Windows XP Home Edition installed on (takes up whole drive)

HDD2 has two partitions. The first partition has Windows Vista Home Premium installed (partition ~220GB) and the other partition has Ubuntu installed (partition 20GB (+ 5GB swap partition)).

XP was installed first, followed by Vista. When Vista was installed it added its own bootloader allowing me to boot into either XP or Vista. Ubuntu was installed last and installed GRUB bootloader

I am able to boot successfully in to all OSes through Grub, However in order for me to boot into XP/Vista I have to first select Windows Vista/Longhorn Loader from the GRUB bootmenu this will then load the Vista Bootloader allowing me to boot either XP or Vista

I was hoping weather it'll be possible to add XP and Vista to GRUB so I can bypass the Vista bootloader. Is this possible at all? Or am I better of Adding Ubunut to Vista's bootloader by using EasyBCD and removing GRUB?
Thanks for any help

It is easy.

Paste the results of these two commands:

> 
less /etc/fstab


> 
less /boot/grub/menu.lst


Adding Vista is as simple as adding a couple lines to a file.

---

### Post by tomtity123 on 2008-01-03
I found this site gives a nice simply guide for dual booting.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

Tom

---

### Post by wildteen88 on 2008-01-03
less /etc/fstab output:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=ec59868e-ec5e-400a-a695-27191513a2ab /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=e9a81e5d-ca35-4cb9-aa66-a6856f2395ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

less /boot/grub/menu.lst output:
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
# kopt=root=UUID=ec59868e-ec5e-400a-a695-27191513a2ab ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec59868e-ec5e-400a-a695-27191513a2ab ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec59868e-ec5e-400a-a695-27191513a2ab ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
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

> Adding Vista is as simple as adding a couple lines to a file.
I want to add XP too.

---

### Post by LaRoza on 2008-01-03
The first command should have been:

```

sudo fdisk -l

```

Sorry.

Add this to the end for Vista:
```

title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

I don't know how the Window boot loader works exactly, so this may not work as I think. I never had a chance (and probably never will) to install XP and Vista.

---

### Post by wildteen88 on 2008-01-03
Output:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde72de72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87a8c42c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       27033   217142541    7  HPFS/NTFS
/dev/sdb2   *       27034       29644    20972857+  83  Linux
/dev/sdb3           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris
```

---

### Post by boban on 2008-01-03
I think wildteen88 doesn't have a problem with booting vista... The problem is about getting all 3 OS'es into the grub menu... 

I have similar problem (xp, xp64 and ubuntu). But I don't think that it is possible to boot both windows installations from grub. I suspect that windows has one bootloader for all windows installation, but I'm not windows guru, so correct me if I am wrong.

---

### Post by wildteen88 on 2008-01-03
> **boban said:**
> I think wildteen88 doesn't have a problem with booting vista... The problem is about getting all 3 OS'es into the grub menu... 

I have similar problem (xp, xp64 and ubuntu). But I don't think that it is possible to boot both windows installations from grub. I suspect that windows has one bootloader for all windows installation, but I'm not windows guru, so correct me if I am wrong.

Yes you are correct I am wanting to boot all Oses from GRUB rather than having two bootmenus

---

### Post by LaRoza on 2008-01-03
> **boban said:**
> I suspect that windows has one bootloader for all windows installation, but I'm not windows guru, so correct me if I am wrong.

It seems that way too.

Because the Windows installations are not on the same disk, you could wipe the Windows bootloaders, reinstall both of them separately, reinstall grub and go from there.

You should unplug the drive no being redone for this, for simplicity.

You can use the Super Grub Disk to restore the Windows boot loaders, then use [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to reinstall grub.

---

### Post by wildteen88 on 2008-01-03
Umm..I might look more into EasyBCD (tool for managing Windows boot loader) and add Ubuntu to it instead and remove GRUB. I can live with the two bootloaders everything works find at the mo.

I am very impressed with Ubunut so far. I had bad experience with Ubuntu before however I was using old hardware then.

Thanks for your help everyone.

---

### Post by wildteen88 on 2008-01-05
Hey guys just to update you that I have successfully managed to add Ubuntu to Vista's Bootloader using EasyBCD and all is well. It was easier than I thought it'll be!

---

