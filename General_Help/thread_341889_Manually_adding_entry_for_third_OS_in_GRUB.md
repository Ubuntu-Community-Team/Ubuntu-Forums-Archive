---
title: "Manually adding entry for third OS in GRUB"
date: 2007-01-19
forum: General Help
---

### Post by CroEragon on 2007-01-19
Recently i got my hands on old 20gb IDE hard-drive i i thought i would try i would tryout few other distros apart from ubuntu without damaging my Ubuntu and Windows XP Home on 160gb SATA drive. I installed Mandriva 2007 One on that hard drive allowing Mandriva to take whole drive cause it will probably be formated again soon, i plan to stay with Ubuntu. When Mandriva installer asked me to chose bootloader i choose GRUB and added Ubuntu. For some reason installer did not rewrite MBR and i thought:  Even better, i just have to add Mandriva in my Ubuntu menu.lst and it will work. I mounted Mandriva root partition in Ubuntu, copied entries from Mandriva menu.lst (leaving out windows one) and added them to Ubuntu menu.lst. I thought: Its same bootloader it recognise same entries, it will be easy.
But it is not. In Grub i now have 3 more options for Mandriva but when i try to chose them it returns error 17, cannot mount selected partitions. I know i have to modify entries but i have no idea what to change. Can anyone please help me about it? 
Here is my menu.lst with non-working mandriva entries:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 5_sequence

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=13b33c38-787f-420f-b2de-f49945fce441 ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet
boot

title Mandriva 2007 One
kernel (hd0,0)/boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

title Mandriva 2007 One-nonfb
kernel (hd0,0)/boot/vmlinuz root=/dev/hdd1 
initrd (hd0,0)/boot/initrd.img

title Mandriva 2007 One failsafe
kernel (hd0,0)/boot/vmlinuz root=/dev/hdd1  failsafe
initrd (hd0,0)/boot/initrd.img


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```
I suspect somethig in line: karnel (hd0,0) but i do not have idea what to change.](*,)

---

### Post by m0u53m4t on 2007-01-19
I warn you, I got this wrong when I tried and had to reinstall GRUB. Be careful, and if you're ever not sure, ask.

---

### Post by markitect on 2007-01-19
Your right it is because of the (hd0,0)  what you need to do is determine where the drive is. check out the device for the mandriva drive the letter part goes to the first number a=0, b=1, etc and the partition number is the second number, note this is numbered from 0 instead of one so hdb1 = (hd1,0) etc.

---

### Post by bernied on 2007-01-19
This is not so hard, you probably just need to change all occurences of (hd0,0) to (hd1,0) in the mandriva entries. Just don't change entries for ubuntu (providing it is working - it is, right?). Make a backup first if you are nervous:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```
then edit the file and change (for example), this:
> title Mandriva 2007 One
kernel (hd0,0)/boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd (hd0,0)/boot/initrd.img
to this:
```
title Mandriva 2007 One
kernel (hd1,0)/boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd (hd1,0)/boot/initrd.img
```
You could make it a little simpler by changing it to a more ubuntu-like style:
```
title Mandriva 2007 One
root (hd1,0)
kernel /boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd /boot/initrd.img
```
I also strongly suggest that you move all those entries so that they are below the automagic area, ie below this line:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
because anything above this line (and below the matching line that says 'begin automagic blah blah') will be wiped out when you next update a ubuntu kernel.

---

### Post by bernied on 2007-01-19
To clarify, the entries that you should move are the mandriva entries, not the ubuntu entries - you want those to get updated when you get a new ubuntu kernel.

---

### Post by CroEragon on 2007-01-19
> **markitect said:**
> Your right it is because of the (hd0,0)  what you need to do is determine where the drive is. check out the device for the mandriva drive the letter part goes to the first number a=0, b=1, etc and the partition number is the second number, note this is numbered from 0 instead of one so hdb1 = (hd1,0) etc.
I changed 0 to 3 because Mandriva root is on hdd1. I also changed 0 to 3 in line below karnel one. I left second 0 in entire because 1=0 in second part and partition is hdd1. After restart i got error 21, i cant remember message. What did i do wrong? Here is copy of changed entries
```
title Mandriva 2007 One
kernel (hd3,0)/boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd (hd3,0)/boot/initrd.img

title Mandriva 2007 One-nonfb
kernel (hd3,0)/boot/vmlinuz root=/dev/hdd1 
initrd (hd3,0)/boot/initrd.img

title Mandriva 2007 One failsafe
kernel (hd3,0)/boot/vmlinuz root=/dev/hdd1  failsafe
initrd (hd3,0)/boot/initrd.img
```



> **bernied said:**
> This is not so hard, you probably just need to change all occurences of (hd0,0) to (hd1,0) in the mandriva entries. Just don't change entries for ubuntu (providing it is working - it is, right?). Make a backup first if you are nervous:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```
then edit the file and change (for example), this:

to this:
```
title Mandriva 2007 One
kernel (hd1,0)/boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd (hd1,0)/boot/initrd.img
```
You could make it a little simpler by changing it to a more ubuntu-like style:
```
title Mandriva 2007 One
root (hd1,0)
kernel /boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd /boot/initrd.img
```
I also strongly suggest that you move all those entries so that they are below the automagic area, ie below this line:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
because anything above this line (and below the matching line that says 'begin automagic blah blah') will be wiped out when you next update a ubuntu kernel. I didn't trie to change Ubuntu ones, they work properly. Also i still didn't try your suggestion, but isn't it wrong to Ubuntu and Manriva have same entries in that part??? In other hand another suggestion didn't work (unless i messed up something) so i dont know. Could just confirm that you are sure it should be 0 not 3 as said in another post?

BTW, Do you mean that my Windows entry will be deleted after new karnel? Cause Windows entry is only after ### END DEBIAN AUTOMAGIC KERNELS LIST line.

---

### Post by markitect on 2007-01-19
You could have some odd device mapping, from a terminal run 
```
sudo grub --probe
```

it will take you to a command line area, simply type quit

then ```
cat /boot/grub/device.map
```

this **should** list what your drives are map to

also at the boot up screen you can select an entry and press e for edit and change the (hdX,Y) part of the entry around to try different stuff.  If mandriva makes a separate boot partition you might find that you need (hd3,2) or something weird like that.

---

### Post by CroEragon on 2007-01-19
> **markitect said:**
> You could have some odd device mapping, from a terminal run 
```
sudo grub --probe
```

it will take you to a command line area, simply type quit

then ```
cat /boot/grub/device.map
```

this **should** list what your drives are map to

also at the boot up screen you can select an entry and press e for edit and change the (hdX,Y) part of the entry around to try different stuff.  If mandriva makes a separate boot partition you might find that you need (hd3,2) or something weird like that.
After entering first, then second command you suggested i get: Error 12: Invalid device requested
Any idea?

EDIT:Never mind, im just stupid i followed your suggestion and after it didnt work i anserwed before using my head. I opened suggested file with gedit from file manager and here is result:```
(hd0)	/dev/hdd
(hd1)	/dev/sda
```
So i really should use 0 not 3 like bernied said.

---

### Post by markitect on 2007-01-19
Looks that way, probably because of the way your SATA controller and IDE are attached, so IDE drives area always first
That is assuming mandriva is on the IDE drive

---

### Post by CroEragon on 2007-01-19
I changed Mandriva entries in this:```
title Mandriva 2007 One
kernel (hd0,1)/boot/vmlinuz root=/dev/hdd1  splash=silent vga=788
initrd (hd0,1)/boot/initrd.img

title Mandriva 2007 One-nonfb
kernel (hd0,1)/boot/vmlinuz root=/dev/hdd1 
initrd (hd0,1)/boot/initrd.img

title Mandriva 2007 One failsafe
kernel (hd0,1)/boot/vmlinuz root=/dev/hdd1  failsafe
initrd (hd0,1)/boot/initrd.img
```
And i get Error 15: File not found

The files vmlinuz and intrid.img mentioned in entries is in  Mandriva's /boot/.
Any ideas?

---

### Post by markitect on 2007-01-19
do a ```
fdisk -l /dev/hdd
```
If it has more then one Linux partition listed try mounting them and seeing if there is a vmlinuz there

then mount each partition listed as linux and from the directory you mounted it run:
```
find -name "vmlinuz*"
```

and the same for initrd*

if it has one that is just vmlinuz use that,
otherwise you may have one that is vmlinux-2.#.###-# depending on your kernel version that will work too

once you find it it will list the path
make the line read ```
(hd0,X)/path
where X is the number corresponding to the regular partition number minus 1
and the path is the exact path returned by find
(you can eaither include the ./ in the beginning of the path or take it off
```

---

### Post by CroEragon on 2007-01-19
output is:```
Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1019     8185086   83  Linux
/dev/hdd2            1020        2434    11365987+   5  Extended
/dev/hdd5            1020        1369     2811343+  82  Linux swap / Solaris
/dev/hdd6            1370        2434     8554581   83  Linux


```
Btw, if anyone will use this discussion to help himself just to let him know command should be used in root privileges: sudo fdisk -l /dev/hdd 

I mounted hdd6 and ran command for finding and i get nothing (not even on partition i know it exist, just anoter command line with myusername@mydesktop). And hdd6 is just home as i suspected. Almost nothing on it.
In Mandriva's /boot/ there is vmlinuz, vmlinuz-2.6.17-5mdvlegacy, karnel.h and more other files. Also there is HUGE system.map file not even similar to Ubuntu's one.

---

### Post by bernied on 2007-01-19
Please re-read my original post. Try (hd1,0), not (hd0,1).

---

### Post by bernied on 2007-01-19
To answer your question about the automagic area, it is defined by the '### BEGIN AUTOMAGIC KERNELS LIST' and 
'### END DEBIAN AUTOMAGIC KERNELS LIST'
Items within this area are updated when you update your kernel or initrd in ubuntu. Configuration settings for this updating are also within this area and are the lines with a sngle '#' at their beginning. Lines beginning '##' are true comments and lines without are commands to grub.

The windows entry is outside this area so will not be updated, this is good. It is probably also good to keep the mandriva entries outside this area.

---

### Post by bernied on 2007-01-19
If you still have trouble, try [this link](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer), for how to use tab-completion in grub. 
You do not need to download a cd, you already have a grub console. Just type 'sudo grub' at the command line to get into the grub console. From there follow Herman's instructions at that link.

---

### Post by CroEragon on 2007-01-20
Thanks bernied your suggestion from first page worked, im now able to boot in Mandriva. And i just have two words to say about it: Mandriva SUCKS. After about 4 hours of trying to use it i was not able to sort out my ADSL router (it worked but VERY slow), I was unable to get any informations about mounting ext3 partition etc. Biggest drawback is too polished Desktop. I have been with it long time on XP i do not need another XP copy that hide everything from you with moderate-good GUI and destroys Linux wth copying XP. Anyway, i think that i will use my second hard drive to test Fiesty Fawn, now i see why is Ubuntu most popular distro out there. 

BTW Since im bound to to do at least one more manual adding could you explain why i put hd1,0 so i understand how it works, and i do not have to ask you about every installation. Maybe, i will be able to help somebody else with that knowledge.:wink:

---

### Post by bernied on 2007-01-20
As far as grub is concerned hd0 is your first disk - to grub this means the primary disk according to your PCs bios. Likewise hd1 is the second disk, according to the bios boot order. hd1,0 is the first partition on the second disk (still according to grub). If your boot order went something like CD, Disk1, Disk2, you might find that grub called your second disk hd2 instead of hd1, because it is now the third device, not the second.

This is a little different to linux, but remember that when grub is operating, linux has not yet booted, so they do not use the same information. Grub is actually a mini operating system in its own right, and has its own language and standards - you should not expect it to follow linux standards because it is independent of linux.

If you are going to be messing about with multiple operating systems (ie more than just one windows/OS-X and one linux), then I suggest you set up a small partition (10MB is enough) that is just for booting. You would only need the grub files in this partition. You can then use this partition to boot everything else. Each of the OSes would then have their own partition and would be self contained there.

I'd also suggest you use the chainloader function of grub (this is the way grub boots Windows). In my understanding this basically restarts the boot process at the location you specify. You have to boot windows this way because windows' boot system is not compatible with grub. But you can boot linux OSes this way, so long as you have set up their bootloader in their own partition. This way you can let each OS manage its own bootloader, because you will have multiple bootloaders. So linux distros that use LILO, for instance, will not need to be adapted to use grub - you just boot to LILO. The important thing here is to make sure that each distro boots from its own partition, not from the master boot record on the first disk. This mbr you will change only once, when you set up your boot partition.

But don't try to do this all now, enjoy linux for a while first. And read that stuff of Herman's on that link in my last post - he is a grubbing genius. And make yourself a grub disk/CD/usb-stick, and make sure you can boot everything you own manually before you install another OS. This is a good grub/booting education in itself.

---

### Post by CroEragon on 2007-01-21
> **bernied said:**
> As far as grub is concerned hd0 is your first disk - to grub this means the primary disk according to your PCs bios. Likewise hd1 is the second disk, according to the bios boot order. hd1,0 is the first partition on the second disk (still according to grub). If your boot order went something like CD, Disk1, Disk2, you might find that grub called your second disk hd2 instead of hd1, because it is now the third device, not the second.

This is a little different to linux, but remember that when grub is operating, linux has not yet booted, so they do not use the same information. Grub is actually a mini operating system in its own right, and has its own language and standards - you should not expect it to follow linux standards because it is independent of linux.

If you are going to be messing about with multiple operating systems (ie more than just one windows/OS-X and one linux), then I suggest you set up a small partition (10MB is enough) that is just for booting. You would only need the grub files in this partition. You can then use this partition to boot everything else. Each of the OSes would then have their own partition and would be self contained there.

I'd also suggest you use the chainloader function of grub (this is the way grub boots Windows). In my understanding this basically restarts the boot process at the location you specify. You have to boot windows this way because windows' boot system is not compatible with grub. But you can boot linux OSes this way, so long as you have set up their bootloader in their own partition. This way you can let each OS manage its own bootloader, because you will have multiple bootloaders. So linux distros that use LILO, for instance, will not need to be adapted to use grub - you just boot to LILO. The important thing here is to make sure that each distro boots from its own partition, not from the master boot record on the first disk. This mbr you will change only once, when you set up your boot partition.

But don't try to do this all now, enjoy linux for a while first. And read that stuff of Herman's on that link in my last post - he is a grubbing genius. And make yourself a grub disk/CD/usb-stick, and make sure you can boot everything you own manually before you install another OS. This is a good grub/booting education in itself.

Thanks, now i understand why GRUB labels disks in different way. Just 2 more questions. Is it possible to move current Ubuntu GRUB installation to boot partition as you suggested and do you know any link that explains creating GRUB entries by yourself, not copying it like i did, so when i install another Linux OS i will be able to generate entry for that os without copying its own entry from its menu.lst.

---

### Post by bernied on 2007-01-21
I suggest you read through [Herman's grub page](http://users.bigpond.net.au/hermanzone/p15.htm)
It should answer most of your questions. And you could try out his super grub disk as well.

Just do a little bit at a time, and always know how to reverse what you did, in case you make a mistake.

---

