---
title: "Ubuntu 7.10 and Vista dual boot menu problem"
date: 2008-02-19
forum: General Help
---

### Post by PsyCLown89 on 2008-02-19
Hey guys, hope this is the correct section to post this under.

I finally decided to check out Linux and see how it is.etc So far my experiance with Linux hasnt been very good and I havent even been able to get into a full installed version. :(

I wanted to run a Vista/Linux dual boot and I first installed Vista then today I installed Linux and it installed 100% then it asked if I wanted to stay in the live CD boot or restart and I decided to stay in the live CD boot as I was browsing some site and then after that I went to the power button and clicked on restart then I noticed my PC booted back into Vista, so I restarted again and to my amazment there was no boot menu.

So now I have a problem. I have Vista installed and I have installed Linux. But there is no boot menu. I also didnt bother creating a swap file partition for Linux as I have 4GB and dont need since im going to be running 32bit, but I dont think that would make any difference would it?

So is there anyway I can maybe get a dual boot menu so I can get into Linux? 
I dont mind reinstalling Linux and I would prefer not to have to reinstall Vista as iv formated twice in the last 2 days...dont feel liek doing it again :mad:

Anyhelp would be greatly appreciated! :D

---

### Post by monty_13 on 2008-02-19
I'm hyaving the same problem! Please could someone help!

---

### Post by seventhc on 2008-02-19
I would try booting to the live cd and open a terminal...*Applications>Accessories>Terminal* and paste these commands in, then post the output of each.
```
sudo fdisk -l
``````
gksu gedit /boot/grub/menu.lst
```

---

### Post by PsyCLown89 on 2008-02-19
> **seventhc said:**
> I would try booting to the live cd and open a terminal...*Applications>Accessories>Terminal* and paste these commands in, then post the output of each.
```
sudo fdisk -l
``````
gksu gedit /boot/grub/menu.lst
```

Sudo fdsik code
```

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
```

When I typed that gksu code in the terminal, it opened up a blank document. The menu.lst document. Seems to be with notepad or something similar.

Is that what you wanted to know?

**EDIT:** Ok, well when I opened the partition which I installed Linux onto and went to boot>grub then opened up the menu.lst this is what it says.

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
# kopt=root=UUID=8b8c11fe-23c6-4529-b414-c5052e8742cb ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8b8c11fe-23c6-4529-b414-c5052e8742cb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8b8c11fe-23c6-4529-b414-c5052e8742cb ro single
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
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I think this is what you wanted?

---

### Post by seventhc on 2008-02-19
the letter L in lower case not number 1

Did you tell it not to install grub during the install???
Just paste my commands in don't type them. so from the live cd, navigate to this page and copy and paste the commands into the terminal.

Note: none of these commands have numbers if it looks like a one, its an L in lowercase (menu.lst too LST but lower case.) :)

---

### Post by PsyCLown89 on 2008-02-19
> **seventhc said:**
> the letter L in lower case not number 1

Did you tell it not to install grub during the install???
Just paste my commands in don't type them. so from the live cd, navigate to this page and copy and paste the commands into the terminal.

Ok, here.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbac52dbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120033041920 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a841a83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9494    76258304    7  HPFS/NTFS
/dev/sdb2            9495       14562    40708710   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x191cd9ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    7  HPFS/NTFS

```

All my drives and their partitions.

Im also currently in Linux live CD boot.
Also during the install I got nothing about grub.

Ok, so all the commands in Linux dont have numbers in them?

---

### Post by seventhc on 2008-02-19
I just meant the commands I was having you do didn't have numbers, other commands might.

OK so you have grub and linux is on your hdd, your menu also states that it has a 10 second timeout option which means it should stay on the menu screen before it boots into the default selection.
Normally unless you change something it would boot into ubuntu unless you choose windows from the menu. 
hmmm...
are you in front of the computer while it's rebooting? I ask in case your just not there when the menu is shown, then it boots to default selection.

---

### Post by PsyCLown89 on 2008-02-19
> **seventhc said:**
> I just meant the commands I was having you do didn't have numbers, other commands might.

OK so you have grub and linux is on your hdd, your menu also states that it has a 10 second timeout option which means it should stay on the menu screen before it boots into the default selection.
Normally unless you change something it would boot into ubuntu unless you choose windows from the menu. 
hmmm...
are you in front of the computer while it's rebooting? I ask in case your just not there when the menu is shown, then it boots to default selection.

Oh, ok. :D

Yeh, the 1st time I booted I wasnt. Then after that iv always been at my PC and its never shown me any boot menu.
I have had a dual boot many times, but that was with various windows Operating Systems.

It also seems as if Vista is in charge of the boot menu.etc as I set it to 10sec under Vista. Also Windows doesn't recognize the Linux file format and therefor it wouldnt pick it up.

Also I have partitioned the 120GB HDD and have Installed Vista onto the 1st partition and Linux onto the 2nd partition then I should have around 2GB free unpartitioned space on the 120GB HDD.

My 2x 320GB HDDs dont have any OS on them...only data.

---

### Post by zipperback on 2008-02-19
If you want to setup your system for dual boot then you need to do a little reading on the subject.

read the information I posted on the following thread.
[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

Good luck.
- zipperback
:popcorn:

---

### Post by seventhc on 2008-02-19
Well from the output you posted, your windows does have the boot flag. It's the '*' in the output. I don't dual boot anymore, so I would wait for someone who does to tell you what settings need to be adjusted.
If you installed ubuntu second it always makes itself default so I'm a bit confused why it didn't this time.
I have dual booted vista and ubuntu before, but I didn't have to change anything, it just worked.
There are plenty of people here that dual boot, and they will be able to get your settings correct though.
You did install ubuntu last, right??

---

### Post by My_World on 2008-02-19
Woaw, its been almost 2 years since I last visited these forums!

If it wasn't for you asking, I would have passed...

Anyway, SWAP....
Yes you can go without a swap partition, but that it like turning off virtual memory in Windows. You are going to take a massive hit in performance, so don't come crying "Vista is OMW faster than Ubuntu", you have been warned!

Now for the menu, the GRUB menu.

Either reinstall and make sure that GRUB is installed to the MBR, or do the following.

Boot into the live CD and issue the commands:
```

sudo su [PRESS ENTER]
mkdir /mnt/hdd [PRESS ENTER]
mount /dev/sdb2 /mnt/hdd [PRESS ENTER]
cd /mnt/hdd [PRESS ENTER]
mount --bind /dev /mnt/hdd/dev
mount -t proc /proc /mnt/hdd/proc [PRESS ENTER]
chroot /mnt/hdd /bin/bash [PRESS ENTER]

```

If you have any errors here just give me a shout, you know where to reach me, post the error here and let met know...

Now to install the boot loader, GRUB:
```

grub [PRESS ENTER]
root (hd1,1)      [PRESS ENTER]     #This is the /dev/sdb2 that has the Linux partition
setup (hd0) [PRESS ENTER]
quit [PRESS ENTER]

```
According to your fdisk output the above should work.

EDIT:
Did not see you posting the menu.lst file, so it should be fine.

That should do it, unless I made a typo....
:lolflag:

```

shutdown -r now [PRESS ENTER]

```

This will reboot the machine and you will have the GRUB boot loader to choose you operating system with a 10 second delay according to your menu.lst file.

Shout if you're struggling.

---

