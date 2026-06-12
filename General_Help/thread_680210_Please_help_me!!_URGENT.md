---
title: "Please help me!! ****URGENT****"
date: 2008-01-27
forum: General Help
---

### Post by makinasvp on 2008-01-27
Oh my goodness guys, this is the situation....

I originally had (hopefully still have) Windows XP 32bit sp2 and I decided to install ubuntu 7.10 and dual boot it. Now I have followed the steps from:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

I did everything the way it said, I created a swap of at least 512MB (600MB to be exact), and then the primary for ubuntu 7.10 and set it to root (/) exactly the way the tutorial told me to do it. Once ubuntu was installed, I did the update system and installed the Nvidia driver from Restricted Drivers Manager, and then when I restarted the system WINDOWS XP WAS GONE!!!! Only 3 options showed that I can select...

-Ubuntu
-Ubuntu (recovery)
-MemTest

NO WINDOWS XP!!

I cannot find my Windows XP CD anywhere I am so screwed. I am in a CAL clan for Counter-Strike Source and now everything is gone. All my music, everything. But here's the thing I do not understand, I re-inserted the LIVE CD of ubuntu 7.10, and look at the screenshot I took...

[IMG]http://i20.photobucket.com/albums/b248/SlowSRT/Screenshot-3.png[/IMG]

It says it's still there!!?? WTF??? What is going on? Did I lose everything? Or is there hope for me and someone here is able to help me...

Please anybody, help me!! PLEASE!!!

---

### Post by digital_exhaust on 2008-01-27
Try the [SuperGrub]("http://supergrub.forjamari.linex.org/?section=home#help") disc... you should be able to save the partition that Xp is on, but until your able to save that partition, DO NOT write anything to the your hard drive... otherwise, your going to have to dig up an XP install cd somewhere and try a repair...

---

### Post by makinasvp on 2008-01-27
But what did I do wrong? Why isn't Windows XP on the list of OS's for me to select from when I restart my computer? How can I fix that? Are you sure SuperGrub will work and that's exactly what I need to do? Or is there anything simpler that I can do at this point? Thank you so much for your fast response btw

---

### Post by espressopigeon on 2008-01-27
I'm pretty sure that windows doesn't like paging/swap file sizes of a not base 2 number, I don't know if this is affecting the problem at hand, just a suggestion.

Could you post the contents of this file: 
```
/boot/grub/menu.lst
```
that's where grub looks for the operating systems to list on the menu, so Windows might not have gotten in there for some reason.

---

### Post by digital_exhaust on 2008-01-27
You'll have to outline the *exact* steps that you took during the Ubuntu install..... when you first got to the screen you posted above, what did you do? It's obvious that Grub installed, but for some reason it's not picking up XP....

---

### Post by makinasvp on 2008-01-27
> **espressopigeon said:**
> I'm pretty sure that windows doesn't like paging/swap file sizes of a not base 2 number, I don't know if this is affecting the problem at hand, just a suggestion.

Could you post the contents of this file: 
```
/boot/grub/menu.lst
```
that's where grub looks for the operating systems to list on the menu, so Windows might not have gotten in there for some reason.
Do I need to take out the LIVE CD and restart it in order to type this in the terminal? Or can I just do this from the Live session?

---

### Post by digital_exhaust on 2008-01-27
> **espressopigeon said:**
> I'm pretty sure that windows doesn't like paging/swap file sizes of a not base 2 number, I don't know if this is affecting the problem at hand, just a suggestion.

True, but I have ignored this many times in the past and haven't had any problems at all....I'm pretty sure the SuperGrub disc can fix this... I haven't had to use it in this manner before, but according to the documentation in the faq, it should...

---

### Post by espressopigeon on 2008-01-27
Yes, you can do it from a livecd

---

### Post by makinasvp on 2008-01-27
> **espressopigeon said:**
> Yes, you can do it from a livecd

```
diouf@diouf-desktop:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
diouf@diouf-desktop:~$
``` 

This is what I get...

---

### Post by makinasvp on 2008-01-27
In the tutorial link in my first post, I do see that I did ONE thing different from the tutorial... I don't know if that matters or not, but after creating the SWAP, when I created the main partition for linux, in the tutorial it shows as PRIMARY and PRIMARY... When I created mine, I believe LOGICAL and PRIMARY were selected...

---

### Post by espressopigeon on 2008-01-27
Put "sudo nano" before that, the file will open in a console text editor

---

### Post by makinasvp on 2008-01-27
Ok this is my "menu.lst"

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
# kopt=root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by espressopigeon on 2008-01-27
I don't see a place in the tutorial where primary and primary were selected.

Ah, just what I thought, Windows didn't show up in menu.lst, so hence, no Windows menu option.

---

### Post by ferdostar on 2008-01-27
Before doing whatever do a backup of your grub menu
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

---

### Post by makinasvp on 2008-01-27
> **espressopigeon said:**
> I don't see a place in the tutorial where primary and primary were selected.

In my first post, click on the tutorial link and look at STEP 8, the image right below STEP 8, instead of PRIMARY I selected LOGICAL and BEGINNING. But in the tutorial it says to select PRIMARY and BEGINNING...

---

### Post by makinasvp on 2008-01-27
> **ferdostar said:**
> Before doing whatever do a backup of your grub menu
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

Done. Please help me!!

---

### Post by Raccoon1400 on 2008-01-27
get to the file by navigating to it graphically. you can view it  this way, but need to log in as root to edit it.

---

### Post by makinasvp on 2008-01-27
> **Raccoon1400 said:**
> get to the file by navigating to it graphically. you can view it  this way, but need to log in as root to edit it.

It's already up, look at post #12. Now I do not know what to do... please somebody help me, I really need the stuff that's in Windows XP... :(

---

### Post by ferdostar on 2008-01-27
Can you put the output of
```
fdisk
```

---

### Post by makinasvp on 2008-01-27
> **ferdostar said:**
> Can you put the output of
```
fdisk
```
```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
diouf@diouf-desktop:~$ 

```

Here you go...

---

### Post by Majorix on 2008-01-27
I think you are stuck - notice how it says "unknown" for the amount of space used by the ntfs partition. That's not a good thing.

---

### Post by digital_exhaust on 2008-01-27
> **Majorix said:**
> I think you are stuck - notice how it says "unknown" for the amount of space used by the ntfs partition. That's not a good thing.

I agree, and I really think your going to need to find an XP install CD and try a repair install, that should re-write the XP bootloader and you can start over from there...

---

### Post by makinasvp on 2008-01-27
> **digital_exhaust said:**
> I agree, and I really think your going to need to find an XP install CD and try a repair install, that should re-write the XP bootloader and you can start over from there...

What about super grub? How can I use that?

---

### Post by michaelzap on 2008-01-27
The fact that XP doesn't show up in Grub doesn't mean that it's gone, so don't panic yet. For whatever reason Grub didn't detect your Windows installation during the install, but you should be able to add it to your Grub menu and reboot and see if you now get it as an option. If you do, choose it and see if it boots (and if you don't, try pressing e at the Grub menu and trying different partitions until you're sure that you're trying to boot the Windows partition).

I don't know that it's necessarily such a big deal that your Windows partition shows up as an unknown size right now. Usually when I've repartitioned a Windows drive and added Ubuntu to it I've found that the first time that I boot into Windows it runs chkdsk and repairs the partition table (since it's shocked to find taht it's a lot smaller than the last time it started up). So if you are able to boot from your WIndows partition and it wants to run the chkdsk utility, let it and hopefully that will be that.

It's always a good idea to have a Windows CD handy just in case you need to repair your installation. Usually that just means running chkdsk, fixboot, and/or fixmbr from the repair console, so any XP CD should do (I've never had to do a full repair installation in this circumstance). If you don't have a WIndows CD, you can borrow or download one to do this (you're not going to use it to install WIndows; just to repair your existing installation).

---

### Post by AndyCooll on 2008-01-27
Try:
```
sudo fdisk -l
```

You may need to add Windows to the bottom of your grub list. It should look something like this:
> title    Microsoft Windows XP
root     (hd0,0)
savedefault
makeactive
chainloader    +1

Where the (hd0,0) relates to your Windows partition.

:cool:

---

### Post by Mze on 2008-01-27
From the image posted in thread 1, looks like swap and ext3 are at the front of the drive. I usually partition leaving WinXP in front of the partition and then use the free space created on the right of the bar. 

Is that the way you partitoned the drive? 

I guess WinXP doesn't like being moved around thus the inability to boot it.

---

### Post by espressopigeon on 2008-01-27
add this to menu.lst:
```

title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```
this should at least make XP show up in the grub menu, then you can try what michaelzap said. That 4 in hd(0,4) is your partition number.

---

### Post by michaelzap on 2008-01-27
> **digital_exhaust said:**
> I agree, and I really think your going to need to find an XP install CD and try a repair install, that should re-write the XP bootloader and you can start over from there...

A repair install is much more drastic than I would recommend at this point. That overwrites the installed version of XP with the files on the CD, which means you'll need to do all the updates again and probably need to reinstall many applications. Just booting into the recovery console from an XP CD and doing chkdsk /r, fixboot, and fixmbr is what I'd recommend to start with (which will mean that Grub will no longer work, but that's easy to reinstall later after the panic has passed).

---

### Post by ferdostar on 2008-01-27
1) Think you should pick some windows boot cd
2) Not sure, but you can try to add something looking like that in your /boot/grub/menu.lst

```
default 1

timeout 10

title Microsoft Windows XP Professional
root (sda5, 1)
savedefault
makeactive
chainloader +1
```

after ```
## ## End Default Options ##
``` and before

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Than restart, but one more time not sure about the issue

---

### Post by digital_exhaust on 2008-01-27
> **michaelzap said:**
> A repair install is much more drastic than I would recommend at this point. That overwrites the installed version of XP with the files on the CD, which means you'll need to do all the updates again and probably need to reinstall many applications. Just booting into the recovery console from an XP CD and doing chkdsk /r, fixboot, and fixmbr is what I'd recommend to start with (which will mean that Grub will no longer work, but that's easy to reinstall later after the panic has passed).

Your 100% correct... sorry for being so vague. I think I was focusing on the fact that the OP currently has no access to an XP install disc, and I should have been a bit more concise with my recommendations.... 

Good advice, and thanks for being a bit more specific!

---

### Post by makinasvp on 2008-01-27
There's 3 different from you guys...

```
default 1

timeout 10

title Microsoft Windows XP Professional
root (sda5, 1)
savedefault
makeactive
chainloader +1
```

```
title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

```
title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +
```


Which one do I try guys?

---

### Post by ferdostar on 2008-01-27
> **makinasvp said:**
> There's 3 different from you guys...

```
default 1

timeout 10

title Microsoft Windows XP Professional
root (sda5, 1)
savedefault
makeactive
chainloader +1
```

```
title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

```
title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +
```


Which one do I try guys?

Mine is if, you had Windows XP [COLOR="Red"]Professional[/COLOR] and I wrote root sda5 seeing that you had the ntfs partition on [COLOR="Red"]/dev/sda5[/COLOR], but you can try also with [COLOR="Red"]hd0, 1[/COLOR]

---

### Post by makinasvp on 2008-01-27
And also, how do I save the menu.lst after I make the changes? I get a yellow bar at the top with a message that says:

```
Could not save the file /boot/grub/menu.lst

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```

---

### Post by espressopigeon on 2008-01-27
sudo is the key. if you're using a graphical editor: ```
gksudo *name of editor*
``` if not: ```
sudo *name of editor*
```

To ferdostar: I think grub uses hd(x,y) only, where x is the disk number, and y is is the partition counting from 0 not 1. Hence, sda5=hd(0,4).

---

### Post by ferdostar on 2008-01-27
> **espressopigeon said:**
> sudo is the key. if you're using a graphical editor: ```
gksudo *name of editor*
``` if not: ```
sudo *name of editor*
```

To ferdostar: I think grub uses hd(x,y) only, where x is the disk number, and y is is the partition counting from 0 not 1. Hence, sda5=hd(0,4).

To esspressopigeon: absolutely right about the grub syntax ](*,) Sorry, just didn't pay intention when was writting, I've just saw, that his ntsf partition was sda5

---

### Post by makinasvp on 2008-01-27
Ok I tried:

```
default 1

timeout 10

title Microsoft Windows XP Professional
root (sda5, 1)
savedefault
makeactive
chainloader +1
```

When I restarted the computer, the menu for Windows XP Professional showed up, but I got:

```
Error 23: Error while parsing number

Press any keys to continue...
```

Something of that sort. I'm gonna try the other one now... the:

```
title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

---

### Post by makinasvp on 2008-01-27
Same thing...

Error 23: Error while parsing number

Press any keys to continue...

---

### Post by Mze on 2008-01-27
what's the output of?

sudo fdisk -l

---

### Post by makinasvp on 2008-01-27
> **Mze said:**
> what's the output of?

sudo fdisk -l

```
diouf@diouf-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          73      586341   82  Linux swap / Solaris
/dev/sda2              74       60800   487789627+   f  W95 Ext'd (LBA)
/dev/sda5           25497       60800   283579348+   7  HPFS/NTFS
/dev/sda6              74       25496   204210184+  83  Linux

Partition table entries are not in disk order
diouf@diouf-desktop:~$ 

```

---

### Post by makinasvp on 2008-01-27
And I also typed blkid and cat /etc/fstab into the terminal, and this is what I get... I don't know if this is useful or not...

```
diouf@diouf-desktop:~$ blkid
/dev/sda1: UUID="0f731116-9c87-456c-a032-3a3055c44e02" TYPE="swap" 
/dev/sda5: UUID="D2586AE8586ACAB5" TYPE="ntfs" 
/dev/sda6: UUID="a3d25107-1ed0-4a59-8a6a-e41d48fdea0b" SEC_TYPE="ext2" TYPE="ext3" 
diouf@diouf-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=D2586AE8586ACAB5 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=0f731116-9c87-456c-a032-3a3055c44e02 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
diouf@diouf-desktop:~$ 
```

---

### Post by ferdostar on 2008-01-27
have you tried with 
```
title Microsoft Windows XP Professional
root (hd0, 2)
savedefault
makeactive
chainloader +1
```

---

### Post by makinasvp on 2008-01-27
Please help me... I can feel we are so close :(:(

---

### Post by makinasvp on 2008-01-27
> **ferdostar said:**
> have you tried with 
```
title Microsoft Windows XP Professional
root (hd0, 2)
savedefault
makeactive
chainloader +1
```

No not yet...

---

### Post by Mze on 2008-01-27
Your swap drive shouldn't have a boot flag.

The NTFS partition should have a boot flag and the Linux partition should have boot flags. Use the Partition editor on the Live CD to change that.

from the look of things you also have extended fat32 partiton on your drive.
linux is on hd0,5 as per your intial bootmenu paste.

This how to modify your boot menu:

title Microsoft Windows XP
rootnoverify (hd0,4)
chainloader +1
makeactive
boot

let us know how it goes

---

### Post by makinasvp on 2008-01-27
> **ferdostar said:**
> have you tried with 
```
title Microsoft Windows XP Professional
root (hd0, 2)
savedefault
makeactive
chainloader +1
```

I get:

```
Error 12: Invalid Device Requested

Press any keys to continue...
```

---

### Post by makinasvp on 2008-01-27
> **Mze said:**
> Your swap drive shouldn't have a boot flag.

The NTFS partition should have a boot flag and the Linux partition should have boot flags. Use the Partition editor on the Live CD to change that.

from the look of things you also have extended fat32 partiton on your drive.
linux is on hd0,5 as per your intial bootmenu paste.

This how to modify your boot menu:

title Microsoft Windows XP
rootnoverify (hd0,4)
chainloader +1
makeactive
boot

let us know how it goes

Ok I am a noob... lol Please tell me exactly what I need to do, step by step...

---

### Post by Mze on 2008-01-27
Go to System>>>Administration>>Partition Editor 

Top right button of Partition Editor window. Select /dev/sda5 
This should be your NTFS partition from what you've posted.
Under the tab "FLAG" does it read boot? if not "Right click>>Select "Manage flags" and set it to boot.

Same applies to the Linux partiton. ext3

Find the swap partiton from the list and take "Boot" flag off.

---

### Post by makinasvp on 2008-01-27
Wow GParted takes forever to scan devices...

---

### Post by Mze on 2008-01-27
I can't help but think that the swap file created at the front of your drive is most probably the beginning of your woes. 

Gparted usually doesn't take long, post prolly having problems figuring out where the NTFS partition starts and ends.

---

### Post by makinasvp on 2008-01-27
The swag is the only one with a boot flag...
The NTFS didn't have a boot flag, I am trying to adjust things but GParted is very slow, it's been 5 minutes now since I clicked on manage flags > boot for NTFS... I wonder if I should have started unflagging the swap first...

---

### Post by Mze on 2008-01-27
Where you able to boot Ubuntu without the CD initially? If so, no need to flag the linux partition. Just take the boot flag off the swap file. Since Gparted is taking too long.

Edit the boot menu to reflect the change to allow Windows XP to show and then reboot without the CD.

---

### Post by makinasvp on 2008-01-27
Well I just tried to put a boot flag to the NTFS and GParted crashed...Then I re-launched GParted and it still took forever to open BUT...below is a screenshot of what it looks like now...

[IMG]http://i20.photobucket.com/albums/b248/SlowSRT/Gparted.png[/IMG]

What should I do now?

> Edit the boot menu to reflect the change to allow Windows XP to show and then reboot without the CD.

What do I need to do?

---

### Post by Mze on 2008-01-27
set ext3 partition flag to "boot". 

after you've modified the boot menu with command:

sudo nano /boot/grub/menu.lst

and saved changes, try to reboot and lets see.

---

### Post by makinasvp on 2008-01-27
> **Mze said:**
> set ext3 partition flag to "boot". 

after you've modified the boot menu with command:

sudo /boot/grub/menu.lst

and saved changes, try to reboot and lets see.

Ok and when I am in my menu.lst, what exactly do you need me to modify? What do you want me to put there?

---

### Post by Mze on 2008-01-27
find that section where you where playing around with hd(0,4). As instructed by others earlier

and make sure it is still (hd0,4)

Save changes and then reboot. take your live CD out.

---

### Post by makinasvp on 2008-01-27
Right now as you can below it is set to (hd0,2). When I tried to reboot and selected Windows XP Professional, it gave me an error saying "Partition Not Found"...

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
# kopt=root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3d25107-1ed0-4a59-8a6a-e41d48fdea0b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Should I try changing it to (hd0,4) instead of (hd0,2)???

---

### Post by Mze on 2008-01-27
yep.

hd0,4

---

### Post by makinasvp on 2008-01-27
> **Mze said:**
> yep.

hd0,4

Ok I restarted the computer, selected Windows XP Pro and now it says:
```

Error 12: Invalid Device Requested

Press any keys to continue...
```

---

### Post by Mze on 2008-01-27
are you able to boot into Ubuntu from the menu?

---

### Post by makinasvp on 2008-01-27
> **Mze said:**
> are you able to boot into Ubuntu from the menu?

Yes I am, I'm in it right now typing this.

---

### Post by Mze on 2008-01-27
Let's try this in your boot menu::

title Microsoft Windows XP Professional
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

And if this doesn't work then, hey, you've got to grab a WinXP CD or just download one.

Running out of options now.

---

### Post by makinasvp on 2008-01-27
> **Mze said:**
> Let's try this in your boot menu::

title Microsoft Windows XP Professional
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

And if this doesn't work then, hey, you've got to grab a WinXP CD or just download one.

Running out of options now.

Ok I am going to try that. Are you sure that it's (hd0,4) and not 3 or 2 or 1 or 0 or 4 or 5 or 6 or anything like that? Just curious...

---

### Post by Mze on 2008-01-27
Well you could try other numbers. I'm just going by what your fdisk -l shows. It however also states at the bottom of the fdisk command that the partitions aren't in order. So, for sure, give it a shot.

---

### Post by Mze on 2008-01-27
remember that your boot menu shows this for Ubuntu

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)

one can only deduce

---

### Post by michaelzap on 2008-01-27
You can try other numbers right from the Grub menu by selecting the Windows entry and pressing the e key to edit it (this won't permanently change your Grub menu, but it allows you to use different options at boot when necessary).

---

### Post by makinasvp on 2008-01-27
Ok well it didnt work, it still gave me Error 12: Invalid Device Requested...

I now have Win XP CD in and im in the repair... I type chkdsk and then fixboot and it said "The new bootsector was successfully written."

Do I need to type fixmbr now or is there no need?

---

### Post by michaelzap on 2008-01-27
> **makinasvp said:**
> Ok well it didnt work, it still gave me Error 12: Invalid Device Requested...

I now have Win XP CD in and im in the repair... I type chkdsk and then fixboot and it said "The new bootsector was successfully written."

Do I need to type fixmbr now or is there no need?

I usually do all three of those things when I want to be sure that Windows will boot up, but you might not need fixmbr. What did chkdsk tell you? Did it take a while and say that it had repaired problems?

---

### Post by Mze on 2008-01-27
try a reboot first then take it from there.

fixmbr will overwrite Grub, so you would have to reinstall it from the live CD to be able to access Ubuntu again.

---

### Post by makinasvp on 2008-01-27
> **michaelzap said:**
> I usually do all three of those things when I want to be sure that Windows will boot up, but you might not need fixmbr. What did chkdsk tell you? Did it take a while and say that it had repaired problems?
No it didnt take too long, it just said The volume appears to be in good condition and was not checked.
Use /p if you want to check the volume anyway.

Should I try that?

---

### Post by makinasvp on 2008-01-27
Ok well now it says that there's 1 or more errors on the volume...

I typed fixboot and restarted it and Windows gave me same error "Invalid Device Requested", should I try fixmbr? Or what can I do to repair WIndows?

---

### Post by Mze on 2008-01-27
use the fixmbr option then, looks like your best bet.

---

### Post by makinasvp on 2008-01-27
> **Mze said:**
> use the fixmbr option then, looks like your best bet.
Thank GOD it worked!!!! Now I just have to re-installed Ubuntu 7.10 properly. Thanks you guys!!

---

### Post by michaelzap on 2008-01-27
Actually, you probably only need to reinstall GRUB. Your Ubuntu installation should be fine as is. Glad you got through the stressful part...

---

### Post by Mze on 2008-01-27
Well in his situation, a quick install wouldn't hurt. 

Make sure you go about the partition part well or you might get 2 Ubuntu installs.

Good luck.

****
Let's see what your bootmenu looks like after reinstall. :)

---

