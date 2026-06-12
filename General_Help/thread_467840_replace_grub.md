---
title: "replace grub"
date: 2007-06-08
forum: General Help
---

### Post by joriad on 2007-06-08
Ok, I messed up. Not being familiar with some earlier versions of Ubuntu (Warty, Hoary, and Dapper) I wanted to see what they were like. So, out of curiosity,  i installed Warty on my dual boot system that already had Windows Vista and Fiesty Fawn installed. As I should have known this changed the grub, i can boot into Fiesty and Warty but not Vista. As I was only curious to see what Warty was like, I have no intention of keeping it on my system and would like to remove it. However as I have no real experience with grub I am unsure of how to safely go about this. I would like to keep my existing Fiesty and Vista partitions in tact and recognized by grub if at all possible. Any suggestions would be appreciated.  

Thanks.

---

### Post by joriad on 2007-06-08
bump

---

### Post by mbeierl on 2007-06-08
Once booted into Fiesty, can you post the output of the following command:```
sfdisk -l
```  That'll help us recover your boot chain by showing us on which partition Windows is installed.

---

### Post by nealio1000 on 2007-06-08
thats a tricky bit. i have found myself in a similar situation and lost everything because of it. Be very careful which os u are in when you remove the partiton you don't like. after this if you get the error: "NTLDR is Missing" than u messed up. ntldr is the loader for windows. if you do a windows boot fix it still won't fix that. hopefully, if that happens you will still be able to boot into fiesty fawn and maybe fix the situation. i couldn't do that in my situation for i only had two oses (one was linux and one was windows xp). i had deleted linux and then i got that error. so i was basically screwed and had to reinstall everything.

sooo... point of the story is that you are in a delicate situation and hopefully you don't have any emotional attachments to any finals on ure computer

---

### Post by joriad on 2007-06-08
This is the output of sfdisk -l

Disk /dev/hda: 155061 cylinders, 16 heads, 63 sectors/track
Units = cylinders of 516096 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+  30472-  30473-  15358108+   7  HPFS/NTFS
/dev/hda2      30472+ 122113-  91641-  46186875   83  Linux
/dev/hda3     153079+ 155055-   1977-    996030   82  Linux swap / Solaris
/dev/hda4     122114  153078   30965   15606360   83  Linux

---

### Post by mbeierl on 2007-06-08
Okay, so /dev/hda1 is your windows partition.  If you add the following to the end of your /boot/grub/menu.lst you should have your Windows back:
```

title windows vista
rootnoverify (hd0,0)
chainloader +1

```

---

### Post by joriad on 2007-06-08
> **mbeierl said:**
> Okay, so /dev/hda1 is your windows partition.  If you add the following to the end of your /boot/grub/menu.lst you should have your Windows back:
```

title windows vista
rootnoverify (hd0,0)
chainloader +1

```

Am I adding this the the end of the menu.lst file in Warty since I installed that last or in Fiesty? 
This is what is in the Fiesty menu.list. Vista is in the Fiesty menu.lst file but not in the Warty file. I did try to add that at the end of Warty but it couldn't find Vista. I will reboot to Warty and paste what I have in that Grub file and the error that I get.

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
# kopt=root=UUID=a0b26215-1b61-409e-b51b-7f42c0d84992 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a0b26215-1b61-409e-b51b-7f42c0d84992 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a0b26215-1b61-409e-b51b-7f42c0d84992 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a0b26215-1b61-409e-b51b-7f42c0d84992 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a0b26215-1b61-409e-b51b-7f42c0d84992 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by joriad on 2007-06-08
Ok, the error I get when I try to boot Vista is something like "Windows failed to start","The selected entry could not be loaded because the application is missing or corrupt". 

The Warty  menu.lst file reads

 > # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda4 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-6-686 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.8.1-6-686 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-6-686
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-6-686 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.8.1-6-686 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.8.1-6-686
savedefault
boot

title		Memory test
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu 7.04 (7.04) (on /dev/hda2)
root		(hd0,1)
kernel		/vmlinuz root=/dev/hda2
initrd		/initrd.img
savedefault
boot

title		Windows Vista/longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mbeierl on 2007-06-08
I'm wondering if the grub in warty is older.  Try booting into Feisty and doing the following:
```

sudo grub
root (hd0,1)
setup (hd0)
quit

```

---

### Post by joriad on 2007-06-08
> **mbeierl said:**
> I'm wondering if the grub in warty is older.  Try booting into Feisty and doing the following:
```

sudo grub
root (hd0,1)
setup (hd0)
quit

```

That removed Warty from grub but did not get me back into vista. when I try and boot the vista partition it wants to load the windows boot manager but fails.

---

### Post by joriad on 2007-06-09
Solved. I needed to put my Vista disc in and do a recovery of the Vista system. 

Thanks for your help.

---

