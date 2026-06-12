---
title: "GRUB: Error 17 'Cannot Mount Partition'"
date: 2006-12-07
forum: General Help
---

### Post by Octarine on 2006-12-07
Hi, im new here, and i'd apprecite some help please! :) 

Ive just installed ubuntu from the live CD onto a second internal hard drive, which is partioned into:

500Mb Swap for Linux
21Gig for Linux (In EXT2 format)
220Gig for Data (In NTFS format)

My Main harddrive has Windows XP installed and is NTFS format, 29Gigs

When I attempt to boot from the Linux Drive, GRUB comes up
(which I understand is the bootloader)
And gives me an Error 17, which is defined as 'Cannot mount selected partition'

At this point I have not entered into the GRUB menu, I am still in the computers Boot sequence.

I have tried Booting from the Windows hard drive, but I get 'Error Loading Operation System'

What can I do from here to get GRUB working again?

I can still run the Live CD, so can use the terminal.

Thanks in advance,
Octarine

---

### Post by daniminas on 2006-12-07
Check this theread: [http://www.ubuntuforums.org/showthread.php?t=309243](http://www.ubuntuforums.org/showthread.php?t=309243)

17 is when grub can't recognize the type of the file system.

---

### Post by Octarine on 2006-12-07
I try 'find /boot/grub/stage1' in the terminal under grub, but all I get returned is File Not Found...

What now?

---

### Post by bulldog on 2006-12-07
As I understand you have two hard drives?
Which one are you booting from?

Please give us the outcome of ```
sudo fdisk -l (l as in like)
```
And your menu.lst as well please,if you are on the live cd you have to mount your ubuntu install.
So the outcome of the fdisk command is needed to know which partition to mount.

---

### Post by Octarine on 2006-12-07
Here's the output of that..

ubuntu@ubuntu:~$  sudo fdisk -l

Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3737    30017421    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              65       27596   221150758+  17  Hidden HPFS/NTFS
/dev/hdb2   *       27597       30401    22531162+  83  Linux
/dev/hdb3               1          64      514048+  82  Linux swap / Solaris

Partition table entries are not in disk order



And, how do I open menu.lst please?

---

### Post by bulldog on 2006-12-07
> **Octarine said:**
> Here's the output of that..

ubuntu@ubuntu:~$  sudo fdisk -l

Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3737    30017421    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              65       27596   221150758+  17  Hidden HPFS/NTFS
/dev/hdb2   *       27597       30401    22531162+  83  Linux
/dev/hdb3               1          64      514048+  82  Linux swap / Solaris

Partition table entries are not in disk order



And, how do I open menu.lst please?

From which drive are you booting?
This is something I must know to advice the setup of GRUB.
To mount your ubuntu install```
sudo mkdir /mnt/rescue
```
Than```
sudo mount /dev/hdb2 /mnt/rescue
```

Now you have your ubuntu mounted at /mnt/rescue

If you can post your menu.lst```
cat /mnt/rescue/boot/grub/menu.lst
```

---

### Post by Octarine on 2006-12-07
Im Booting Linux from Hard drive 2.

Here's the contents of menu.lst:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hdb2 ro

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

title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by bulldog on 2006-12-07
Yes linux is on hard disk two.
But I want to know on which disk is GRUB installed.
As I look at your menu.lst is GRUB on the first disk.
```
## ## End Default Options ##

title Ubuntu, kernel 2.6.15-23-386
root (hd0,1) <--------
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd0,1)  <-------
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title Ubuntu, memtest86+
root (hd0,1)  <-------
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
rootnoverify (hd1,0)  <---------
map (hd0) (hd1)       <--------- 
map (hd1) (hd0)       <---------
savedefault
makeactive
chainloader +1
```

If you set the ubuntu disk with GRUB as default boot device and you change your menu.lst according 
this example it should work.

Your ubuntu disk is than (hd0) so your ubuntu will start with (hd0,1.
Your windows must be mapped,because windows like to think it's on the first disk.
This will be (hd1) so windows will start by pointing it at (hd1,0)

To change your menu.lst we make a copy first ```
sudo cp /mnt/rescue/boot/grub/menu.lst /mnt/rescue/boot/grub/menu.lst-bak
```
Now to alter your menu.lst```
sudo gedit /mnt/rescue/boot/grub/menu.lst
```
Change the settings according my example,and save the file.
Than reboot and try if it works.

Good luck

---

### Post by Octarine on 2006-12-07
I think GRUb is installed to Disk two. Would this be a problem?

---

### Post by bulldog on 2006-12-07
See my previous post,and you have to change one more thing in your menu.lst,
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1) <------- change this to (hd0,1)
```

---

### Post by Octarine on 2006-12-07
Thanks, ive made the changes, il reboot now and let you know how it goes.

:D

---

### Post by Octarine on 2006-12-07
Okay, that didnt work. Was I supposed to replace the equivalent large piece of text with the large bit that you wrote? 
Because I did that, and it still displays GRUB Error 17...

Any other Ideas?

---

### Post by bulldog on 2006-12-07
Nope you had to change the entry's I changed as an example :D

I put the <------- things after the lines you had to change.

And you have a hidden partition,why is that?

Is this necessary or can you un-hide the partition

Can you give me your menu.lst again?

---

### Post by Octarine on 2006-12-07
Ohhh, Okay. Theyre just changed to (hd0,1) arent they?

---

### Post by bulldog on 2006-12-07
Yes but you have a hidden partition,so it could be that (hd0,1) must be changed into (hd0,0).

What about windows? will it boot?
See previous post also.

---

### Post by Octarine on 2006-12-07
I dont think ive actually chosen to hide that partion, Im not sure whay thats done that.
But, if its the 500Mb partition, then thats the Swap, or the Large one is just Data.
Windows still wont boot either.

Menu.lst is below.

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hdb2 ro

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

title Ubuntu, kernel 2.6.15-23-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
ubuntu@ubuntu:~$

```

---

### Post by bulldog on 2006-12-07
Well the settings for windows should be allright,ubuntu could be (hd0,0) because of the hidden partition.

If windows won't boot,do you get an error message?

Try and set the (hd0,1) for ubuntu into (hd0,0) and try to reboot from your hard disk.

If this will give an error too,I must presume GRUB isn't installed on the ubuntu disk.
No problem though we can reinstall it easely.

---

### Post by Octarine on 2006-12-07
Okay, Il try that now, and also see what message I get for Windows when I try boot that. Thanks!

---

### Post by Octarine on 2006-12-07
Again, that didnt work, and when I try boot windows, i get the message 'error loading operating system'

How do we re-install GRUB then?

---

### Post by bulldog on 2006-12-07
Reinstall GRUB,
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0) <----- watch out with this one
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

Watch the find answer if it says (hd0) setup (hd0) if it says (hd1) setup (hd1)

---

### Post by Octarine on 2006-12-07
Right, thats done, I assume I reboot now, and see how it goes? ;)

---

### Post by Octarine on 2006-12-07
Okay, nothing much has changed, but trying to boot either Windows or Linux, i Get the GRUB Error 17 both times.
Il have a look at this again tommorrow, but any more advice? :)

---

### Post by bulldog on 2006-12-07
You have set the ubuntu disk with grub as boot device I presume?
So windows is on the other disk.

That makes ubuntu on (hd0,1) or (hd0,0)and windows on (hd1,0).
Can't make more out of it I'm afraid,if this is set in menu.lst and it will not boot,what can I do?

Only thing what comes in mind is save your data,whipe all your disks and reinstall from scratch.

You can take a look at fstab if there some fault.
```
cat /mnt/rescue/etc/fstab
```

---

### Post by jerrylamos on 2006-12-07
O.K., running CDLive, Kubuntu 6.10 Edgy, grub then find /boot/grub/stage1 returns (hd0,0).  Is that the Kubuntu CD I'm running??  Or is it the hard drive Windows partition 1??  Any way to tell?

What I really wanted was to put grub on the USB drive, dutifully created  with the appropriate CD files plus a second partition persistent casper-rw.  

How can I get grub to find the stage one located at:

/dev/sda1/boot/grub/stage1

so I can try putting grub on partition one of the USB again?  Grub install previously put all the content of /boot/grub on, I've got a menu.lst on, but it doesn't work on both a desktop and a laptop which claim to be able to boot from removable drives.

BTW, my experience with grub is poor, example install of Xubuntu onto a (different) 2G USB drive goes fine until grub install blows up.  Launchpad bug report with syslogs etc. gets no response.

And yes I battled with SuperGrub CD to either boot the USB drive or chainload into it, and after a bunch of messages grub can't find /dev/sda or else /dev/sda1 or anything else I've tried.  Ubuntu, Kubuntu, and Xubuntu can find it fine.

In the forums I see back in 2005 some people were having luck was it with Breezy on USB, so this is not a new game.  I've only tried Dapper and Edgy.

Thanks for any speculations, Jerry

---

