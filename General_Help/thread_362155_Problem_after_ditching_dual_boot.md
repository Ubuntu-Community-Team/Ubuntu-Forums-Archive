---
title: "Problem after ditching dual boot"
date: 2007-02-15
forum: General Help
---

### Post by Pugwash on 2007-02-15
Hi,

I'm in a bit of a problem. A bit hard to explain but here goes - I decided today to totally get rid of xp (was doing a dual boot with dapper), yes I was that impressed by Ubuntu, I thought the best way to go about it it would be to do a reinstall of ubuntu. I wanted to keep my ubuntu system and settings so I backed up my system using this method before doing the reinstall- [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087) - and stuck the backup file on my external . Then I proceeded to reinstall ubuntu  ,chose to wipe the disk clean and start from scratch. Installation went fine, and afterwards I restored my previous system using the method mentioned in the link above. I restarted my computer but Grub then displayed an error about the partition not being detected or something. So my question is, how do I edit Grub so that it points to the right partition (and just sort out the paritition table in general).  I'm running the livecd now and here's the result from fdisk -l
 :

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

```


Thanks

---

### Post by logos34 on 2007-02-15
Grub is fetching the old menu.lst with the old root partition #, and even if you hit 'e' in grub menu and changed the root and kernel line it probably wouldn't mount anyway because your fstab still lists the old partition #.  So you need to use the livecd to get into and edit those files.  
> 
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst

Change the kopt, groot, root and kernel lines for ubuntu kernels and memtest86 to (hd0,0) and /dev/sda1.

Correct / and swap entries in fstab also.

---

### Post by logos34 on 2007-02-15
Post those two files, if you could.

---

### Post by Pugwash on 2007-02-15
Thanks sorted it, I reinstealled ubuntu again :popcorn: , but before I restored my old system I copied the /boot/grub folder to another location, then copied it back after restore. Seems to be working fine, but it keeps booting into a 386 kernel, how do I change it so it boots into the 2.6.15-27-686 kernel (on a dual core) so I don't have to manually change to it when I boot. Here's menu.lst:

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
# kopt=root=/dev/sda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-28-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-28-686
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

``` 

Appreciate the help. :) 

Cheers

---

### Post by logos34 on 2007-02-15
> Seems to be working fine, but it keeps booting into a 386 kernel, how do I change it so it boots into the 2.6.15-27-686 kernel (on a dual core) so I don't have to manually change to it when I boot.

That's strange...It shows **default   0**, which means it should be booting the first kernel listed (2.6.15-28-686).  If you want the 2.6.15-27 kernel, try **default   4**.  Or reboot and manually choose the kernel you want as the default.  Then go back into menu.lst and change the number to the word 'saved':
**> default   saved**

This tells grub to thereafter default to the last booted kernel.

You can even add a hash (#) mark before the **savedefault** option on the other kernels that you **do not** want Grub to remember.

---

### Post by Pugwash on 2007-02-17
It seems to have sorted itself out :) . Thanks for the help anyway.

Cheers

---

