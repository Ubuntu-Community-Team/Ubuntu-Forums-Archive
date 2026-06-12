---
title: "Partimage, Backup, Restore and Boot"
date: 2008-01-15
forum: General Help
---

### Post by VernerVonTux on 2008-01-15
I recently backed up and restored the ubuntu portion of a dual boot (Ubuntu 7.04 and XP Pro) system that I use to another larger hard drive (I plan to resize). When I have not yet backed up or restored the windows portion of my dual boot system, so perhaps this is caused by some mbr issue by my not doing so yet, but the grub does begin to load on what I have backed up so far, but the grub doesn't completely boot. I get Grub error 22. Is grub error 22 something that is commonly encountered after doing a restore? Can this problem be fixed by me selecting the "restore mbr from image file" option of imagepart? Does this option just pull the mbr from one of the partitions that I backed up, or does it somehow require a special mbr only image file to be made and restored from? Any help that some one could provide would be very greatly appreciated.

---

### Post by navd on 2008-01-15
ok well I have no Idea how that would happen after doing a restore. You might have done something else on accident. 
What you should do is boot into your windows xp cd.
When it asks you to go into repair a windows installation ( f2 it will ask i think ) press f2 :P

THen when you get to command prompt. Login to administrator. ( you need to know your pass )

Now in the command line type *fixmbr*
this should fix your problem.

---

### Post by bodhi.zazen on 2008-01-15
navd's advice will overwrite your MBR installing the windows boot loader.

My guess is that your disk geometry changed. I suggest you try re-installing GRUB

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

You can also try Supergrub : [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by navd on 2008-01-15
or you could reinstall grub.:lolflag:

Though if you are just reinstalling everthing fresh it will work out beautifully because it will get overwritten by grub. Just my 2 cents.

---

### Post by wieman01 on 2008-01-16
**@VernerVonTux:**

There is not much more I can say, but I am writing to say that I did a similar thing yesterday after encountering "Error 17" which prompted me to reinstall GRUB using the Live CD. 

In fact it is very simple if you read the link that "bodhi.zazen" has posted carefully. You just boot from CD, run GRUB, tell it where your Linux partition is, and restart the PC.

If you have problems doing so, please post here, we will help you out.

---

### Post by VernerVonTux on 2008-01-16
Well, I did indeed encounter "Grub Error 17" after I restored the windows partition of my dual boot system to my new hard drive. I did manage to correct this and was able to boot into my linux partition, but when I attempted to boot into windows after selecting it from the grub OS selection screen, the screen just hung there. I decided that perhaps something had gone wrong with my restore attempt so, I booted up with SystemRecue CD, deleted the windows partition expanded the linux partition a bit and created an NTFS partition to restore the windows partition to, and then re-restored the image of my Windows XP partition. 

The restore was successful,but still I was unable to boot into Windows. I then decided to try "fixmbr" from the Windows recovery console which claimed to rewrite the MBR successfully; however, still no luck, no grub this time and windows wouldn't boot. I will reinstall grub again and I suppose I will try to make a fresh image of my old XP partition to restore from. Does anyone think that creating a new image of the XP partition will be a possible way to fix the problem? I should note that the NTFS partition I created to restore windows xp to was created using gparted on "SystemRescueCD", would creating an NTFS partition with Windows be a better option? Any further help anyone could provide would be great, I'm hoping to get this resolved so that I can report back on just what exactly ended up happening. :)

---

### Post by wieman01 on 2008-01-16
> **VernerVonTux said:**
> Does anyone think that creating a new image of the XP partition will be a possible way to fix the problem? I should note that the NTFS partition I created to restore windows xp to was created using gparted on "SystemRescueCD", would creating an NTFS partition with Windows be a better option? Any further help anyone could provide would be great, I'm hoping to get this resolved so that I can report back on just what exactly ended up happening. :)
If Windows does not boot, that's not a good sign, however, please make sure that Windows is still on the same partition as before (in terms of partition sequence number). Please open this file and see for yourself:
> sudo kate /boot/grub/menu.lst
Please post the contents so that we can help you correct it and also post:
> sudo fdisk -l

---

### Post by VernerVonTux on 2008-01-17
Well here is my menu.lst:

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
# kopt=root=UUID=22fd0a9c-07b0-463f-a9b5-47cdc8a8f71a ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=22fd0a9c-07b0-463f-a9b5-47cdc8a8f71a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=22fd0a9c-07b0-463f-a9b5-47cdc8a8f71a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=22fd0a9c-07b0-463f-a9b5-47cdc8a8f71a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=22fd0a9c-07b0-463f-a9b5-47cdc8a8f71a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows XP Service Pack 2
root (hd0,0)
rootnoverify (hd0,1)
makeactive
chainloader +1

```

Here is the output for fdisk -l:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7764    62364298+  83  Linux
/dev/sda2   *        7765       10386    21061215   83  Linux

```

/dev/sda2 should be the windows partition, so idk why it is id'd as "Linux". Any help

df -h on /dev/sda1 and /dev/sda2:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              59G   29G   28G  51% 
/dev/sda2              20G   16G  3.8G  81% /media/ntfswrite

Hopefully somebody else can see something causing the problem :)

```

---

### Post by wieman01 on 2008-01-17
Two things that I have noticed...

1. It is indeed odd that "/dev/sda2" is recognized as a Linux partition. I think that is wrong.
2. This section needs to be adjusted:
> title Windows XP Service Pack 2
[COLOR="Red"]root (hd0,1)[/COLOR]
[COLOR="Red"]#rootnoverify (hd0,1)[/COLOR]
makeactive
chainloader +1
Windows resides on [COLOR="Red"]"/dev/sda2"[/COLOR], therefore that line should read [COLOR="Red"]"root (hd0,1)"[/COLOR] rather than [COLOR="Red"]"root (hd0,1)"[/COLOR]. In addition I have commented out the third line which is OK for the time being.

Please change it and let me know if you can boot Windows.

That being said, how did you back up & restore Windows? What program have you used? Any idea why "fdisk -l" would still refer to it as a Linux partition? That is clearly wrong, but I don't really know how this could happen in the first place.

---

