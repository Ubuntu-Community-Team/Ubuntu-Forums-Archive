---
title: "[SOLVED] GRUB error"
date: 2008-06-30
forum: General Help
---

### Post by abuakel on 2008-06-30
So I used the partition editor in Vista to make a 10 GB partition of unallocated space.
During the installation process of Ubuntu, I clicked the Guided installation that uses continuous free space (the second option).
It went through the whole installation process without a problem, and asked me to reboot. I rebooted and I now get:

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22
```

How do I get the Vista back with all the files intact and Ubuntu installed with a dualboot on the same 10 GB partition?

---

### Post by abuakel on 2008-06-30
anyone? please help

*bump*

---

### Post by unutbu on 2008-06-30
We need a bit more information to help you. Please boot from the LiveCD. Open a terminal, then post the output of 

```
sudo fdisk -l
```

---

### Post by Magoffire on 2008-06-30
Are you trying to say that you tried installing both OSs on the SAME partition?

---

### Post by WRDN on 2008-06-30
> **Magoffire said:**
> Are you trying to say that you tried installing both OSs on the SAME partition?

When you use the largest free continuous space, Ubuntu installs on the unallocated space, not the same partition as another OS.

abuakel, please could you post the complete contents of your menu.lst file. To do this, boot from the LiveCD (or anything else you can access the files on), and go to the location - /boot/grub/menu.lst
Then, just copy and paste the contents.

---

### Post by abuakel on 2008-06-30
> **WRDN said:**
> When you use the largest free continuous space, Ubuntu installs on the unallocated space, not the same partition as another OS.

abuakel, please could you post the complete contents of your menu.lst file. To do this, boot from the LiveCD (or anything else you can access the files on), and go to the location - /boot/grub/menu.lst
Then, just copy and paste the contents.

sorry it took me so long, I had to find a creative way of getting the results since the computer with the GRUB error doesn't have internet.

Here are the results for the sudo fdisk -l

```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1311    10485760    7  HPFS/NTFS
/dev/sda3   *        1311       21063   158660608    7  HPFS/NTFS
/dev/sda4           21063       38914   143382528    f  W95 Ext'd (LBA)
/dev/sda5           21063       38914   143381504    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30d3dd7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23391   187882496    7  HPFS/NTFS
/dev/sdb2           23392       24792    11253532+   5  Extended
/dev/sdb5           23392       24727    10731388+  83  Linux
/dev/sdb6           24728       24792      522081   82  Linux swap / Solaris

Disk /dev/sdc: 8017 MB, 8017412096 bytes
16 heads, 32 sectors/track, 30584 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30584     7829488    c  W95 FAT32 (LBA)
```


Edit: Sorry WRDN, I misread what you asked and quoted you for the question of unutbu.
I don't see a grub folder in the /boot/ directory.. here is the URL of the screenshot:
[http://abuakel.googlepages.com/Screenshot-boot-FileBrowser.png](http://abuakel.googlepages.com/Screenshot-boot-FileBrowser.png)

---

### Post by abuakel on 2008-06-30
sorry about the 'bump' again..
but, *bump*

---

### Post by drs305 on 2008-06-30
If you have booted from the live cd, you are going to have to mount the partition with your linux OS.

Open a terminal and run these commands. Replace "sdaX" with the partition with you linux OS on it. If you don't know, post the results of "sudo fdisk -l" and someone can help you:

```
sudo mkdir /temp
mount /dev/sdaX /temp
cat /temp/boot/grub/menu.lst
```

---

### Post by abuakel on 2008-06-30
> **drs305 said:**
> If you have booted from the live cd, you are going to have to mount the partition with your linux OS.

Open a terminal and run these commands. Replace "sdaX" with the partition with you linux OS on it. If you don't know, post the results of "sudo fdisk -l" and someone can help you:

```
sudo mkdir temp
mount /dev/sdaX /temp
cat /temp/boot/grub/menu.lst
```

I did post my results for "sudo fdisk -l" it's on an earlier post..but here it is again:

```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1311    10485760    7  HPFS/NTFS
/dev/sda3   *        1311       21063   158660608    7  HPFS/NTFS
/dev/sda4           21063       38914   143382528    f  W95 Ext'd (LBA)
/dev/sda5           21063       38914   143381504    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30d3dd7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23391   187882496    7  HPFS/NTFS
/dev/sdb2           23392       24792    11253532+   5  Extended
/dev/sdb5           23392       24727    10731388+  83  Linux
/dev/sdb6           24728       24792      522081   82  Linux swap / Solaris

Disk /dev/sdc: 8017 MB, 8017412096 bytes
16 heads, 32 sectors/track, 30584 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30584     7829488    c  W95 FAT32 (LBA)
```

---

### Post by drs305 on 2008-06-30
It would appear the partition you want to mount to retrieve the /boot/grub/menu.lst resides on "sdb5" so that is the one you want to mount.

---

### Post by abuakel on 2008-06-30
> **drs305 said:**
> It would appear the partition you want to mount to retrieve the /boot/grub/menu.lst resides on "sdb5" so that is the one you want to mount.

For learning purposes.. how do you know?

Edit: I rand the commands you gave me and received this:

$ sudo mkdir temp
$ sudo mount /dev/sda5 /temp
fuse: failed to access mountpoint /temp: No such file or directory

Edit 2: sorry, I typed in the wrong command. please disregard.

---

### Post by drs305 on 2008-06-30
In this case, it is fairly easy because you only have two linux partitions. I am making the assumption that grub was installed in the linux partition (we'll see). So it should be on the main linux partition. It wouldn't be in the swap partition. If you had mulitple linux partitions it would not be as easy.

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23391   187882496    7  HPFS/NTFS
/dev/sdb2           23392       24792    11253532+   5  Extended
**/dev/sdb5           23392       24727    10731388+  83  Linux**
/dev/sdb6           24728       24792      522081   82  Linux swap / Solaris

```

---

### Post by abuakel on 2008-06-30
> **drs305 said:**
> If you have booted from the live cd, you are going to have to mount the partition with your linux OS.

Open a terminal and run these commands. Replace "sdaX" with the partition with you linux OS on it. If you don't know, post the results of "sudo fdisk -l" and someone can help you:

```
sudo mkdir temp
mount /dev/sdaX /temp
cat /temp/boot/grub/menu.lst
```

I ran the correct commands, unlike last time.. and got this result:
```

$ sudo mkdir temp
$ sudo mount /dev/sdb5 /temp
mount: mount point /temp does not exist
```

Edit: thanks for the explanation.

---

### Post by drs305 on 2008-06-30
> **abuakel said:**
> I ran the correct commands, unlike last time.. and got this result:
```

$ sudo mkdir temp
$ sudo mount /dev/sdb5 /temp
mount: mount point /temp does not exist
```

Edit: thanks for the explanation.

Try making the directory again. I missed the "/"
sudo mkdir /temp

If it doesn't work this time, run "**ls /** and see if the directory "temp" is listed.

---

### Post by abuakel on 2008-06-30
After typing these commands:

sudo mkdir /temp
sudo mount /dev/sdb5 /temp
sudo cat /temp/boot/grub/menu.lst

I got these results:

```
ubuntu@ubuntu:~$ sudo cat /temp/boot/grub/menu.lst
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
# kopt=root=UUID=ecafd647-4905-4716-ab3b-b392f969ec93 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ecafd647-4905-4716-ab3b-b392f969ec93 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ecafd647-4905-4716-ab3b-b392f969ec93 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


```

---

### Post by soccerboy on 2008-06-30
I don't know the exact solution but I remember reading somewhere that for vista, grub has to be chainloaded from vista bootloader to allow access to both os.  Just thought it might help

---

### Post by abuakel on 2008-06-30
> **soccerboy said:**
> I don't know the exact solution but I remember reading somewhere that for vista, grub has to be chainloaded from vista bootloader to allow access to both os.  Just thought it might help

That'll be added to the numerous reasons why I greatly abhor Vista lol :D

---

### Post by soccerboy on 2008-06-30
i hear you.  I have stayed with windows XP for my occasional windows needs (I do development for windows).  Can't get businesses to switch as fast as my household.

---

### Post by abuakel on 2008-06-30
> **drs305 said:**
> Try making the directory again. I missed the "/"
sudo mkdir /temp

If it doesn't work this time, run "**ls /** and see if the directory "temp" is listed.

by the way.. it worked perfectly..
THANKS a lot.. lol, you saved my a$$

---

### Post by drs305 on 2008-06-30
You marked this thread solved but if you are still having problems, read on ...

Grub thinks that windows is on the third partition of the first drive and linux is on the 5th partition of the second drive. Due to grub's methodology, these two are designated (hd0,2) and (hd1,4), which is what grub shows.

Grub Error 22 means grub is having problems locating partitions. At this point, I'll refer you to another post rather than recopy the commands. It will run the "sudo grub" command and take you through a restoration. Try it and then come back here. I'll edit this post to put down the commands but without the explanation. 

So now please refer to this link unless someone has already responded in this post:
[How to restore Grub from a live Ubuntu cd.  ]("http://ubuntuforums.org/showthread.php?t=224351")

That post, in short:
**sudo grub**
At grub prompt:
**find /boot/grub/stage1**
Input result in:
**root (hd?,?)**
**setup (hd0)**
**quit**

---

### Post by abuakel on 2008-06-30
Thanks, I've bookmarked that page since I've gotta go to a friends house and install a dual boot of Ubuntu and Vista. I've never dual booted.. on my laptop, I just wiped XP since I didn't care from it with the Guided Installation by using the whole disk :popcorn:

The reason why I dual booted on my Vista box was because I wanted to make sure I knew how to handle everything in case anything went wrong at my friend's house.
And, now, I've figured it out thanks to this thread and that thread you linked me to.. thanks again.

---

### Post by abuakel on 2008-07-01
> **drs305 said:**
> You marked this thread solved but if you are still having problems, read on ...

Grub thinks that windows is on the third partition of the first drive and linux is on the 5th partition of the second drive. Due to grub's methodology, these two are designated (hd0,2) and (hd1,4), which is what grub shows.

Grub Error 22 means grub is having problems locating partitions. At this point, I'll refer you to another post rather than recopy the commands. It will run the "sudo grub" command and take you through a restoration. Try it and then come back here. I'll edit this post to put down the commands but without the explanation. 

So now please refer to this link unless someone has already responded in this post:
[How to restore Grub from a live Ubuntu cd.  ]("http://ubuntuforums.org/showthread.php?t=224351")

That post, in short:
**sudo grub**
At grub prompt:
**find /boot/grub/stage1**
Input result in:
**root (hd?,?)**
**setup (hd0)**
**quit**


I guess it's not solved anymore.. lol, you were right.
I've followed what you suggested and followed the commands in the link you've attached, but I still get the same GRUB error.

---

### Post by drs305 on 2008-07-01
Is the Vista root still listed as (hd0,2) in your current menu.lst? You might try swapping it and the one listed for the Dell Utility Partition, making Vista (hd0,0). That is where windows often resides, but who knows.

Sorry you aren't getting any more responses. Although I have a dual-boot machine, I've not had grub errors with it. Hopefully you will get some experienced windows users to help you here.

---

### Post by abuakel on 2008-07-01
> **drs305 said:**
> Is the Vista root still listed as (hd0,2) in your current menu.lst? You might try swapping it and the one listed for the Dell Utility Partition, making Vista (hd0,0). That is where windows often resides, but who knows.

Sorry you aren't getting any more responses. Although I have a dual-boot machine, I've not had grub errors with it. Hopefully you will get some experienced windows users to help you here.

It's alright.. 
This is the menu list right?
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
# kopt=root=UUID=ecafd647-4905-4716-ab3b-b392f969ec93 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ecafd647-4905-4716-ab3b-b392f969ec93 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ecafd647-4905-4716-ab3b-b392f969ec93 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

---

### Post by drs305 on 2008-07-01
Yes, that's it. At least you have had practice mounting the linux partition with the livecd...

---

### Post by abuakel on 2008-07-01
> **drs305 said:**
> Yes, that's it. At least you have had practice mounting the linux partition with the livecd...

haha, I've learned soo much just with this error. :popcorn:

I've figured out where Ubuntu is. but how can I tell where the Vista root is?

```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1311    10485760    7  HPFS/NTFS
/dev/sda3   *        1311       21063   158660608    7  HPFS/NTFS
/dev/sda4           21063       38914   143382528    f  W95 Ext'd (LBA)
/dev/sda5           21063       38914   143381504    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30d3dd7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23391   187882496    7  HPFS/NTFS
/dev/sdb2           23392       24792    11253532+   5  Extended
/dev/sdb5           23392       24727    10731388+  83  Linux
/dev/sdb6           24728       24792      522081   82  Linux swap / Solaris

Disk /dev/sdc: 8017 MB, 8017412096 bytes
16 heads, 32 sectors/track, 30584 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30584     7829488    c  W95 FAT32 (LBA)
```

---

### Post by abuakel on 2008-07-01
I fixed my problem by going into the BIOS and disabling RAID or putting RAID on auto.. 

Unutbu informed me that "RAID is for making multiple hard drives seem like one (for better throughput and data reliability). Given that you have Vista on one hard drive and Ubuntu on the other, you are using the two hard drives as independent devices. This disqualifies you for RAID."

soo, after putting it on auto, I was able to boot into Ubuntu, but a new problem occurred with Vista.. it just won't boot.

[COLOR="Red"]Edit:[/COLOR] Computers are strange things.. I re-enable RAID to see if Vista would work.. and low and behold, it did!!.. along with Ubuntu.. This has given me the biggest head ache since getting USB support working in Virtualbox. lol

[COLOR="Red"]Edit 2:[/COLOR] ^^ Computer's aren't strange things.. Microsoft Vista is the strange one. 

This has been officially solved <-- and hopefully I'm not speaking too soon like last time, where the next day, I was back with GRUB Error 22. But I've rebooted and rebooted into both systems various times, without problem.. so I'm hoping it'll stay that way.

---

