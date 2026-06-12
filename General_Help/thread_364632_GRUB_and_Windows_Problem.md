---
title: "GRUB and Windows Problem"
date: 2007-02-18
forum: General Help
---

### Post by Goober on 2007-02-18
Hello Everyone!

I think I have a fairly simple problem here, which should mean that the solution will be simple.  I recently did a complete overhaul of my computer, and installed Windows first, and then Edgy, to ensure that GRUB was there, and recognized Windows.  

One slight problem with this - GRUB recognized Ubuntu, but not my Windows XP installation.  I can't load into Windows now (The only reason I need to is to reformat my iPod which I somehow corrupted or something with gtkpod - but that is another story.)  What I need to do sounds fairly simple to me - edit /boot/grub/menu.lst so that I can have WinXP as an option to boot into, and, well, boot into it. Here is my gedit/boot/grub/menu.lst:

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
# kopt=root=UUID=3c65ea68-a0ee-4697-b0e9-ecbb09b9919a ro
# kopt_2_6=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-10-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-10-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

If anybody could tell me how to add my WinXP installation in here, I would muchly appreciate it!  Thanks a lot!

---

### Post by kpkeerthi on 2007-02-18
can u post the output of ```
 sudo fdisk -l 
```

---

### Post by Goober on 2007-02-18
```

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5099    40957686   83  Linux
/dev/hda2            5100        5227     1028160   82  Linux swap / Solaris
/dev/hda3            5228        9383    33383070    f  W95 Ext'd (LBA)
/dev/hda4   *        9384       19929    84710745   83  Linux
/dev/hda5            5228        9383    33383038+   7  HPFS/NTFS

```

hda5 is WIndows (Obviously).  The linux partition with the * should be my current install, the other Linux HD is swap, and the last is an install of Edgy that I managed to corrupt.

---

### Post by kpkeerthi on 2007-02-18
1. Open terminal
2. Type
```

gksudo gedit /boot/grub/menu.lst

```
3. Copy/Paste the below contents to the end of the file 
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title		Windows XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```
4. Save, exit, reboot. GRUb should now list and be able to load Windows

---

### Post by Goober on 2007-02-18
Hello,

I am not sure why, but that did not work.  It gave me an error on start up, something about an "Invalid Device Requested".  I am honestly not sure what happened.  I know that WinXP installation was a clean install, and it was working.

Thanks for your help thus far, but do you have any suggestions as to what i should do now?

---

### Post by kpkeerthi on 2007-02-19
Did you see Windows booting and died with that error (the blue screen of death) or Windows didn't boot at all?

---

### Post by Goober on 2007-02-19
Hello,

Windows simply failed to boot period.  I clicked on the Windows XP in GRUB, and got the following message, presumably from GRUB, at the top of the screen:

"Error # - Invalid Device Requested"

I forget what it said exactly, and what error code it was, but it was something similar.  Then it took me back to GRUB.  Looking at the script you gave me, I am wondering if the hd(0,4) is correct.  If Windows XP is on the 5th partition, shouldn't that be hd(0,5)?

Thank you for your continued assistance.

---

### Post by Resurrection on 2007-02-19
Unless I'm mistaken, doesn't Grub number drives AND primary partitions starting from 0?

So wouldn't it need to say:

```
root          (hd0,2)
```

Also, aren't there problems with W95 if its not on a primary partition of the first hard drive?  It would appear you have it on an extended partition.

---

### Post by Patrick K on 2007-02-19
hd0,0 is the same drive and partition as hda1. The first is BIOS speak, the second is Linux speak. So hd0,4 isthe same partition as hda5.

---

### Post by kpkeerthi on 2007-02-19
As Patrick said...
hda1 -> hd0,0
hda2 -> hd0,1
hda3 -> hd0,2
hda4 -> hd0,3
hda5 -> hd0,4

Hope you get the idea. Not sure why Windows didn't boot though.

---

### Post by Goober on 2007-02-19
I understand ... which means that my install of WinXP is messed.  Or my Harddrive.  Wonderful.  

Thanks a lot for your help everyone.

---

