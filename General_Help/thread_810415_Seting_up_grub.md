---
title: "Seting up grub"
date: 2008-05-28
forum: General Help
---

### Post by FoX_HunteR on 2008-05-28
ok, i now have 2 HDDs, one with linux and the other with XP...
i plan on using XP only for games,

anyways, the pc boots fine,
it uses the linux drive and used grub to boot,

my question is, how do i setup grub to have XP as a boot option?

heres my boot list so far:

```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 ro quiet splash vmem=256
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title 		Windows XP
root		(hd1,0)
makeactive
chainloader 	+1 

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

how do i fill out the rest of the XP option to make it boot from the second HDD with XP on it?

its been so long since iv used XP that i cant even remember which file it uses to boot...
boot.ini maybe?

---

### Post by pointone on 2008-05-28
```
title 		Windows XP
root		(hd1,0)
makeactive
chainloader 	+1
```

That's all you need to boot XP, normally. The "chainloader" option takes care of starting the Windows bootloader--you don't need to point to specific files like with Linux entries. What happens when you select the Windows XP option from the GRUB menu?

---

### Post by zvacet on 2008-05-28
Put Windows enrties  below this line

### END DEBIAN AUTOMAGIC KERNELS LIST

so your menu list will look like 

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 ro quiet splash vmem=256
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title 		Windows XP
#root		(hd1,0)
#makeactive
#chainloader 	+1 

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST        
title         Windows
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1




Save file and close it.After reboot you should see option to boot in windows in grub.

---

### Post by FoX_HunteR on 2008-05-29
ok, well i changed it, but still no good,
i know the HDD is working, i can access it here through bunty,

when i select Windows XP from the menu, it juat says "Starting Up" or whatever it is that it says when its loading, and just stays there...
then i hit alt + ctrl + del to reboot and just boot into bunty...

how can i check to make sure my windows is ok on my other HDD?
or at least the boot method for windows anyways...

if i change that HDD to the boot device drub still loads up but errors...
could there somehow be a bad version of grub on my other HDD?
if so, how do i piss it off so windows boots normally?

---

### Post by FoX_HunteR on 2008-05-30
anyone?

---

### Post by meierfra. on 2008-05-30
Post the output of

```
sudo fdisk -l
```
(l is a lowercase L)

Also did you erase any partitions when you installed Ubuntu?

---

### Post by FoX_HunteR on 2008-05-31
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29ef16c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc467c467

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS
```


i tried not to touch that HDD to make sure i was able to go back to what i had...
but seems like it might have grub installed on it...
the 80GB HDD is the freshly formated one purely for linux,
and ill be using the 200GB HDD for windows...
id rather not have to format it if possible, theres about 150GB of crap on there i need...

---

### Post by meierfra. on 2008-05-31
fdisk and menu.lst look fine. Maybe you could post the windows part of "menu.lst" so that we can check for misprints.


> ut seems like it might have grub installed on it...

I don't think so. Since menu.lst says (hd0,0) and you can boot into Ubuntu, this means that you are booting from the ubuntu drive and grub is installed on the ubuntu drive.


What happens when you change the boot order in the bios, so that you boot of the Windows Drive? 

If this does not get you into windows and you  have  Windows CD, I suggest to boot into the recovery console (you need to press "r"  after the CD is all the way booted)

Then type


```
fixboot
```

and 

```
fixmbr
```

---

### Post by FoX_HunteR on 2008-05-31
well the fixboot command worked, or appeared to...
the fixmbr killed everything..
now i cant boot into either,
im running linux straight from the disk to do this...

what the hell happened to ubuntu?
for the first time ever, it was working 100% and now its broken again???
when i look at the files on the linux HDD, there are only 4 of them!
and all 4 have weird names, and all appear to be locked!

how do i get ubuntu back to the way it was?
im not re-installing it, i liked it the way it was...

---

### Post by meierfra. on 2008-05-31
Sounds like "fixboot" formated your ubuntu partion and put the  boot files there. 

Did you get any warnings from "fixboot"?

Could you post the output of "sudo fdisk -l"?


Click on testdisk in my signature and see whether it can detect your ubuntu partition  and files.

---

### Post by meierfra. on 2008-05-31
Had you  tried to boot from the Windows drive, before you did "fixboot"? With what result?

---

### Post by FoX_HunteR on 2008-05-31
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29ef16c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc467c467

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

```

ok, well i tryed to boot into windows from the windows HDD,
it still came up with grub, but it wouldnt boot anything...
so i tried your idea, i ran fixboot and it was ok,
but stilll no windows,
so i tried fixmbr and then everything buggered up...

how do i use the testdisk thing?

---

### Post by FoX_HunteR on 2008-05-31
ijust tried the fix grub thing in ur siggy,
now it will load grub up when i boot but when i select bunty it just stays at the splash screen with the bar bouncing from left to right...

---

### Post by meierfra. on 2008-05-31
fdisk looks normal and  grub seems to be working. 
testdisk is a little tricky. But since  your partition table seems to be o.k, lets run a file system check first: (make sure your ubuntu partition is unmounted for this)

```
sudo e2fsck -C0 -pv  /dev/sda1
```

---

### Post by FoX_HunteR on 2008-05-31
```
/dev/sda1: clean, 169160/4685824 files, 1494114/18729774 blocks
```
not sure what the means...

---

### Post by meierfra. on 2008-05-31
That means that  e2fsck thinks your partition is just fine, and does not even bother to check it.  But that isn't always true. Try

> sudo e2fsck -C0 -pfv  /dev/sda1

(the f "forces" a file check, you can use "man e2fsck to figure out what the letters mean)

---

### Post by FoX_HunteR on 2008-05-31
```
  169160 inodes used (3.61%)
    1226 non-contiguous inodes (0.7%)
         # of inodes with ind/dind/tind blocks: 8651/142/0
 1494114 blocks used (7.98%)
       0 bad blocks
       1 large file

  132145 regular files
   17692 directories
      69 character device files
      26 block device files
       3 fifos
     102 links
   19209 symbolic links (18084 fast symbolic links)
       7 sockets
--------
  169253 files

```

---

### Post by meierfra. on 2008-05-31
File systems seems to be ok. Partition table looks fine.   


Lets try to remove the splash screen during boot-up. Then you might get some useful error messages:

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst
```
(Please report any errors)

Look for the first appearance of

title  ubuntu......
root (hd0,0)
kernel .....      splash quiet ....
intitrd

remove  splash and quiet
Save the file.

If this failed for some reason, you can also remove "splash quiet" at the Grub menu during boot up:

Select  ubuntu,  do not press "enter",  but press "e"  to "edit". At the new screen select the second line and press "e" again. Make the changes. Press "enter" and then "b" to boot.

---

### Post by FoX_HunteR on 2008-05-31
ok, well the last line it says for ages is this:

```
[  111.051524] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:UB HID core driver
```

then after a while it comes up with this:

```
Check root=bootarg cat /proc/cmdline or missing modules, devices: cat/proc/modules is /dev
Alert! /dev/disk/by-uuid/cfc2919b-4747-4d12-a7cb-3ca261630bc0 does not exist. dropping to a shell!
```

then it has something about a BusyBox v1.1.3

im not sure what any of this means,
and some spelling could be off since i had to wright it all down then re-type it...

---

### Post by meierfra. on 2008-05-31
Did "gksudo gedit /ubuntu/boot/grub/menu.lst" work ?

Try this:  

```
sudo blkid /dev/sda1
```

This will give you the "UUID" for /dev/sda1. If it is different from

"UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 "

then  replace all "UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0" in  "/ubuntu/boot/grub/menu.lst" and in  "/ubuntu/etc/fstab"  by "/dev/sda1"

So   for example

"root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 "

needs to replaced by

"root=/dev/sda1"


To edit the files: 
```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
sudo gedit /ubuntu/boot/grub/menu.lst
sudo gedit /ubuntu/etc/fstab
```

---

### Post by FoX_HunteR on 2008-06-01
```
ubuntu@ubuntu:~$ sudo blkid /dev/sda1
/dev/sda1: UUID="cfc2919b-4747-4d12-a7cb-3ca261630bc0" SEC_TYPE="ext2" TYPE="ext3" 

```

"gksudo gedit /ubuntu/boot/grub/menu.lst" didnt do anything, it came up with a blank file...

---

### Post by meierfra. on 2008-06-01
I had left out "sudo mkdir /ubuntu" in my origial instructions. So you might try

> sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
sudo gedit /ubuntu/boot/grub/menu.lst

just to see whether you can access "menu.lst"

But I'm at the end of my wisdom. Everything you checked (fdisk, e2fsck, blkid) turned out  normal. 

What happens if you click on the icon for the "ubuntu" partition (where should be one on your desktop or in "Places->Computer")? Are you still unable to see any of your ubuntu files? 

Are you able to see any of windows files, when you click on the icon for the Windows parttion?

Try booting into recovery mode.

Sorry, I don't have any promising suggestion. You might have to start thinking about reinstalling.

---

### Post by meierfra. on 2008-06-01
I'll do some research and see whether I can find any cases where fixboot damaged Ubuntu.

---

### Post by meierfra. on 2008-06-01
Sorry, can't find anything. I just don't see how fixboot could have done any damage to ubuntu unless you would run "fixboot X:" where X is the drive letter of your ubuntu partition. 
Now I just tested on my computer, what happens in this case. Well "e2fsck" found all kinds of errors, but was able to fix them. Since e2fsck didn't find anything wrong with your ubuntu partition, I can only conclude that  you did not run fixboot on your ubuntu partition.

But then neither fixboot nor fixmbr would have touched you ubuntu partition.

[B]So  I believe that your Ubuntu problems are unrelated to you Windows problems.

Did you have any Ubuntu updates lately? There was a kernel update in the last few days which also caused "busy-box" problems.[/B]

---

### Post by FoX_HunteR on 2008-06-01
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
timeout		7

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
# kopt=root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 ro

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

title		Ubuntu 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 ro quiet splash vmem=256
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cfc2919b-4747-4d12-a7cb-3ca261630bc0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Windows XP
root		(hd1,0)
makeactive
chainloader 	+1 
```

well i see that that is the menu.lst that i used to try get windows to work,
but after i completed those commands, i went to see if i could find the same file myself on the linux HDD but its gone???
i can see the windows one, but i can no longer see the linux one...

iv tried booting it in every mode, nothing works,
recovery was the first thing i tried...

theres a possibility that it buggered after that last update,
so i might re-install ubuntu... thankfully iv done it like 9 times beforehand,
it seems to still be rather unstable

well thanks for your help anyways, ill just recover windows when i can find the right CD, and ill format and re-install ubuntu...

cheers
Brett

---

### Post by meierfra. on 2008-06-01
Very strange. It seems  that there is nothing wrong with windows and also nothing wrong with Ubuntu. Except what you can't boot them. So there probably is an easy fix,  but I do not have   the slightest idea what it could be.

Maybe a miracle happens and somebody reading  this thread understands what is  going on.

Good luck with your reinstalling.

---

### Post by zvacet on 2008-06-01
I read this ans see that **meierfra** tried hard to help you,so I don´t put much hope in this one,but you can try it beforer you decide to do reinstall.For last time try to reinstall grub

```
sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,0)
grub> setup (hd0)
```

---

