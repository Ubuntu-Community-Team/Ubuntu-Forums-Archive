---
title: "Boot order in GRUB is wrong, can't  seem to fix it."
date: 2006-11-27
forum: General Help
---

### Post by geek_Man on 2006-11-27
Hey y'all, I've been trying for a long time to get GRUB to work. I've been using Super GRUB Disk for a while, it works fine, but I'd like to use GRUB. So here's the deal, I've installed Ubuntu (works great) only when I try to boot I get the dreaded "Grub loading, please wait... Error 17" message. Now I've been doing a lot of stuff trying to fix it, but it seems that it's looking in the wrong HDD. Here's my setup: I've two hard drives one internal and one external, hda (the internal IDE drive) has two partitions, hda1 is a FAT (recovery) partition and hda2 has XP. Sda has three partitions, sda1 is NTFS (backup) for XP, sda2 is Linux, and sda3 is the swap partition. Sda is the drive I have GRUB installed on, not the MBR of the first one. I've tried to reinstall GRUB to different drives, setup (hd0) and setup (hd1). And I think I've tried different root schemes (or whatever it's called). But whatever I do, I always get that message. So I'm thinking it's looking in the right partition, but in the wrong drive. And here's another thing, no matter what boot order the drives are in SGD always says it's booting from hd1,1. Wouldn't that change with the boot order? :-k I'm sure I'll get it to work eventually, but this just seems kind of weird. Sorry about the huge post, I just wanted to make sure that you guys know exactly how I'm doing this. Thanks in advance!

P.S. I can post my menu.lst or the output of fdisk if you want. I didn't wanted to make the download time of this page to be like 20 minutes. ;)

---

### Post by Spano on 2006-11-27
I think I understand your partitioning scheme, but could you go ahead and post the two files you mentioned?

---

### Post by geek_Man on 2006-11-27
Sure thing. Here's the WHOLE file:

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
timeout		20

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
# kopt=root=/dev/sda2 ro

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

title		Ubuntu Desktop
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu Desktop (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu Desktop (Old)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu Desktop (Old recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Stupid OS's:
root

title     	Windows XP
root 		(hd0,1)
map 		(hd1) (hd0)
map 		(hd0) (hd1)
chainloader +1

```

------------------------------

And here's what fdisk -l says:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21889   175823361    7  HPFS/NTFS
/dev/sda2           21890       36350   116157982+  83  Linux
/dev/sda3           36351       36481     1052257+  82  Linux swap / Solaris

Disk /dev/hda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         665     5027368+   b  W95 FAT32
/dev/hda2   *         666       25840   190323000    7  HPFS/NTFS

Hope this helps and thanks a lot for the reply! :)

---

### Post by CatKiller on 2006-11-27
EDIT: Sorry misread the question. This might help someone though, so I'll leave it in.

Something that occured to me that might help is to use the command **find /vmlinuz** from a GRUB prompt to identify for sure which drive, as far as GRUB is concerned, has the Linux kernel on. Also, you've probably already found it, but [this page]("https://help.ubuntu.com/community/GrubHowto") might help you understand some of what's going on. I certainly don't, since I've not had to fiddle with GRUB myself.

Good luck!

Also, if you put big chunks of text within [CODE] tags, the forum puts them in a scrolly box, which is a bit neater.

[I]If you move your **Stupid OS's:** section above your **### BEGIN AUTOMAGIC KERNELS LIST** line you should be set, and it should stay the same after a kernel update - just changing the **default num** doesn't, since the entry you want moves.

I should probably point out that I've never done this myself, but you were going to make a backup of the file anyway, right?[/I]

---

### Post by geek_Man on 2006-11-27
Yeah, I have a backup copy. Will moving that section actually fix it?

---

### Post by Spano on 2006-11-27
This
```
title Ubuntu Desktop
root (hd1,1)
```
is pointing to this
```
/dev/sda2 21890 36350 116157982+ 83 Linux
```
So I don't understand what the problem would be.  Must admit booting from an external hard drive is beyond my experience, but I know it's possible. Hopefully someone with more knowledge can help.
I did come across this:[http://www-static.cc.gatech.edu/~quocminh/linuxtips/installlinux.html](http://www-static.cc.gatech.edu/~quocminh/linuxtips/installlinux.html)
Read section II and III.
If anything occurs to me I'll post back.
Good luck

---

### Post by geek_Man on 2006-11-27
I can't even access the menu, that's why I think it's looking at the wrong drive. I'll have a look at the link though. Thanks!

---

### Post by CatKiller on 2006-11-27
> **CatKiller said:**
> Something that occured to me that might help is to use the command **find /vmlinuz** from a GRUB prompt to identify for sure which drive, as far as GRUB is concerned, has the Linux kernel on. 

Actually, I just tried this myself, and it didn't work. **find /boot/grub/stage1** did though. If you can't get to a grub prompt from the hard drive, you can use grub on the live install cd by entering **sudo grub** into a terminal. I've never used the Super GRUB disk - does that let you interactively configure GRUB too?

---

### Post by geek_Man on 2006-11-27
Yeah, Super GRUB Disk is great. I haven't used every bit of it since I just use it for what I need. If you mess up your MBR it'll fix that, you can temporarily (I don't know if you can do it permanently though) change the menu.lst and then boot it. You can then change it once you're in. It's pretty neat. But anyway, yeah I know how to do all that stuff, finding stage1 and all that. I didn't see the edit, I'll have a look. Thanks again!

---

### Post by geek_Man on 2006-12-02
Okay, hang on to all of you who are watching this thread. I'm still working on it.

EDIT: See next page.

---

### Post by geek_Man on 2006-12-02
Alright CatKiller (or to anyone else who might know), I can't seem to use mkinitrd. I was looking around and seems I should use mkinitramfs instead. Should I?

---

### Post by geek_Man on 2006-12-02
Okay, I made a new initrd.img. I changed the link in '/' to the right file. Boots fine in SGD, but STILL doesn't work on it's own. Would anyone know if it has anything to do with my device.map file? Just in case, here it is...```
(hd1) /dev/sda
``` I've changed it to hd0 too. Any ideas?

---

### Post by bulldog on 2006-12-02
Don't know if you tried this already,but I'm gonna put my 2 cents in here.

If GRUB is located in the MBR of your external drive,it should point to (hd0,1).
You have to alter your fstab too,to make it point to (hd0,1).

I'm curious if you can boot windows from GRUB because it should point to a wrong device either.
This should be (hd1,1) if I'm not mistaken.

---

### Post by geek_Man on 2006-12-03
So my fstab *should* look like ```
(hd0,1)  /dev/sda2
``` I thought that fstab pointed to drives (or bootsectors), not partitions. Maybe I'm wrong, I'll have to try it. Thanks, man.

EDIT: My bad, I thought you were talking about my device.map (I get those files mixed up). I'll have a look at my fstab (my *real* one ;) ).

---

### Post by geek_Man on 2006-12-03
Okay, here's my fstab: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                               <dump>  <pass>
proc            /proc           proc    defaults                                0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro              0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46          0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46      0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46      0       1
/dev/sda3       none            swap    sw                                      0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto                         0       0

``` 
I don't think anything's wrong, but if there is, please tell me. Sorry that it's so messy.

---

### Post by geek_Man on 2006-12-03
When I was trying to get GRUB to work (again) earlier today, I noticed that when I have the int. HD as the first drive, grub tells me that /boot/grub/stage1 is in hd0,1. And when my ext. HD was the first to boot, grub said that /boot/grub/stage1 was on hd1,1. THUS proving that GRUB *is* looking on the wrong drive all the time. I must be missing something here... :-|

---

### Post by geek_Man on 2006-12-12
There wouldn't be a GRUB guru out there, would there?

---

### Post by geek_Man on 2006-12-17
Anyone? :|

---

### Post by geek_Man on 2007-01-02
Hellooooooo?

---

