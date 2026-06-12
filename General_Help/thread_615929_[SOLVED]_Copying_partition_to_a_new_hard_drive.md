---
title: "[SOLVED] Copying partition to a new hard drive"
date: 2007-11-17
forum: General Help
---

### Post by macaholic on 2007-11-17
Today I installed a new 500gb hard drive in my Mac Pro. It is currently formatted under a ext3 file system. I want to copy ALL the files from my current Ubuntu Partition to my new hard drive. Then ubuntu would have an entire hard drive to itself. What is the easiest way to do this?

---

### Post by mdurham on 2007-11-17
sudo cp -ax source destination
that should do it

---

### Post by macaholic on 2007-11-17
Will I then be able to boot off of the drive then, in other words does it make a bootable clone?

---

### Post by mdurham on 2007-11-17
> **macaholic said:**
> Will I then be able to boot off of the drive then, in other words does it make a bootable clone?

Probably not. You must put GRUB on the MBR and you will most likely have to edit /etc/fstab and maybe /boot/grub/menu.lst, to reflect the new partition's position on the system.

---

### Post by macaholic on 2007-11-18
> **mdurham said:**
> Probably not. You must put GRUB on the MBR and you will most likely have to edit /etc/fstab and maybe /boot/grub/menu.lst, to reflect the new partition's position on the system.
Here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b1802837-2b87-4992-92cd-60dc968d18d8 /               ext3    defaults,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
and here is my /boot/grub/menu.lst:
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
# kopt=root=UUID=b1802837-2b87-4992-92cd-60dc968d18d8 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
```
What would I have to change if the location of the new drive is /dev/sdb?
As far as installing GRUB goes, how would I go about doing so on the new hard drive after I copied all the data?

---

### Post by bingoUV on 2007-11-18
I think the safest way is to create an ext3 partition in your new hard disk, say /dev/sdb1.  Copy all your data to this partition. Optionally, you might create a swap partition (I recommend it, at least for hibernation), say /dev/sdb2. 

Now, boot using any linux livecd. Ensure again that your new hard drive is indeed /dev/sdb, otherwise existing data might get overwritten. Do the following as root
```

mkdir /media/sdb1 
mount /dev/sdb1  /media/sdb1

```

Now edit the file /media/sdb1/boot/grub/menu.lst. Change (hd0, 2) which meant /dev/sda3 to (hd1, 0) which means /dev/sdb1. Check the file /media/sdb1/boot/grub/device.map, and see if /dev/sdb maps to hd1 and /dev/sda maps to hd0. 

Then edit the file /media/sdb1/etc/fstab and fix the entry for / to point to /dev/sdb1 instead of /dev/sda3. UUID will have changed, so use /dev/sdb1 for now.  Now
```

chroot /media/sdb1 
grub-install /dev/sdb

```


Hope this works. Anyway, you are not deleting the original partition until this one boots successfully, so you should be safe.

---

### Post by macaholic on 2007-11-18
Alright everything worked until the grub part, when I try grub-install /dev/sdb it outputs "/dev/sdb: Not found or not a block device." Any ideas? Btw, there is nothing in /media/sdb1/dev
P.S. When yo said "UUID will have changed, so use /dev/sdb1 for now." did you mean take my uuid and change it to /dev/sdb1?

---

### Post by bingoUV on 2007-11-18
I was talking about the UUID that was present in the fstab file you posted. The entry that looked like 
```

UUID=b1802837-2b87-4992-92cd-60dc968d18d8 /               ext3   defaults,errors=remount-ro 0       1

```

will have to look like 
```

/dev/sdb1  /               ext3    defaults,errors=remount-ro 0       1

```

For the rest, follow [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) . 
Especially the part where /proc and /dev are mounted inside the directory to chroot into.

---

### Post by macaholic on 2007-11-18
It seems that it semi-wroked. I think it installed GRUB, and when i reboot (I use rEFIt) it gives me boot linux from gd, and boot linux from partition 1. Now, when I boot from partition one, it boots slower, and then when it finally boots, it is still booting from the old partition on the other har drive. Is GRUB pointing it in the wrong direction for what to load?

---

### Post by macaholic on 2007-11-18
Answered my own question, I had to change all the hd0,1s to hd1,0 and all the uuids in menu.lst. Now is working. How long do you think before  I should trash my other partition?

---

### Post by geirha on 2007-11-18
Did you change the UUID=... to /dev/sdb1 in menu.lst too? I would recommend you use the UUID of the new partition instead (both in fstab and menu.lst). You'll find the UUIDs of all partitions by doing ```
ls -l /dev/disk/by-uuid
```

Physically disconnect the old drive and see if it boots up normally, if it does, I'd say it's safe to trash the old partition. :) However, your new harddrive will most likely move from sdb to sda when you disconnect the old, so you must use UUIDs for such a test.

Edit: but of course, grub has hd1,0 now, which might also be changed to hd0,0. You can change that in the grub menu though (during boot), by selecting your ubuntu entry, hit **e**, select the root-line and change it by hitting **e** again. Then **b** to boot with the altered entry (that change will not be saved).

---

