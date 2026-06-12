---
title: "Trouble with Ubuntu Install"
date: 2008-06-01
forum: General Help
---

### Post by CPlusPunk on 2008-06-01
Hello everyone.. I am new to Ubuntu and when I shut down Ubunto it would not restart. I went to a help forum and found out how to restart and recover with the live cd. I thought I had followed the advise as give. However, when I restarted I ended up with (3) versions of ubuntu and had lost all my previous data (I think). What I ended up with is (2) versions of the 8.4 and (1) of the previous version. Can you help me remove (2) of these versions? Recovering my previous data is not that important. If I need to remove all 3 and start over that is also fine. I am running ubuntu and Vista on the same computer. I think this is dual-Boot? Thank you in advance....

---

### Post by SirPerigrin on 2008-06-01
from the terminal 

> gedit /boot/grub/menu.lst

copy the contents of the file into this thread so we can see what is installed.

also post the output of 

> sudo fdisk -l 

so we can see your partition layout

Sorry, forgot its menu.lst , im always getting that wrong...

---

### Post by CPlusPunk on 2008-06-01
WhenI put (gedit /boot/grub/menu.list) into terminal I get a blank file page with Menu.list at the top. 

Here is what I get when I put (sudo fdisk -l)  
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xead6f3c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       17361   137911296    7  HPFS/NTFS
/dev/sda3           17362       20935    28708155   83  Linux
/dev/sda4           20936       24321    27198045    5  Extended
/dev/sda5           24032       24321     2329393+  82  Linux swap / Solaris
/dev/sda6   *       20936       23897    23792202   83  Linux
/dev/sda7           23898       24031     1076323+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by CPlusPunk on 2008-06-01
When i put in terminal (gedit /boot/grub/) I get a message telling me this is a directory.

---

### Post by SirPerigrin on 2008-06-01
enter 

> gedit /boot/grub/menu.lst 

sorry i mistyped earlier and added an exta i to the file name

---

### Post by CPlusPunk on 2008-06-01
Here it is and it is long///

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
# kopt=root=UUID=e66e645e-e719-4218-9951-3793ac638da3 ro

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
# defoptions=quiet splash man apt-get

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e66e645e-e719-4218-9951-3793ac638da3 ro quiet splash man apt-get
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e66e645e-e719-4218-9951-3793ac638da3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e66e645e-e719-4218-9951-3793ac638da3 ro quiet splash man apt-get
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e66e645e-e719-4218-9951-3793ac638da3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75a354b6-5b22-459f-9074-7ea4ee40deb7 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75a354b6-5b22-459f-9074-7ea4ee40deb7 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by meierfra. on 2008-06-01
You only have two versions of ubuntu. But you do have two kernels for Ubuntu 8.04 on the Grub Menu.  Inluded in the last Ubuntu update, was a kernel update. Since sometimes a new kernel can be incompatible with you hardware, the old kernel  is left on the Grub Menu, so that you don't find yourself unable to boot into Ubuntu. This [thread ]("http://ubuntuforums.org/showthread.php?t=814636") contains some more information on the subject.

---

### Post by SirPerigrin on 2008-06-01
Ok, you dont have 3 installs, but 2. the top 4 entrys in the list are the same install just different kernels. this happens when you update the system. the simple way to fix this is to open menu.lst as root

> gksu gedit /boot/grub/menu.lst 

remove the following sections

> 
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=75a354b6-5b22-459f-9074-7ea4ee40deb7 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=75a354b6-5b22-459f-9074-7ea4ee40deb7 ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title Ubuntu 7.10, memtest86+ (on /dev/sda3)
root (hd0,2)
kernel /boot/memtest86+.bin
savedefault
boot 

install GParted

> sudo apt-get update
sudo apt-get install gparted

then use gparted (System > Administration > Partition Editor) to delete /dev/sda3 and /dev/sda5


you can then partition the space leftover from these partitions for media storage or whatever you like. i DO NOT recommend using GParted to resize any partitions, it isn't the safest program.

---

### Post by CPlusPunk on 2008-06-01
The reason I thought I had 3 versions is, when I boot up I am given the option of 2 versions of 8.4 ubuntu, Windows Vista and then the Ubuntu 7.1 version. Listed in that order. If I am understanding you I actually have 2 versions of the 8.4 and the 7.1 listed in the boot options is not actually there but was replaced by one of the 8.4 versions. Is this correct?

---

### Post by meierfra. on 2008-06-01
>  DO NOT recommend using GParted to resize any partitions, it isn't the safest program.
??????????  All I know is that Gparted can cause booting problems if you resize Vista. (see [here]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"))
Any other issues?

---

### Post by meierfra. on 2008-06-01
> If I am understanding you I actually have 2 versions of the 8.4 and the 7.1 listed in the boot options is not actually there but was replaced by one of the 8.4 versions. Is this correct?

No, you have one version of 8.04 (on /dev/sda6 ) and one version on 7.10 (on /dev/sda3)

---

### Post by SirPerigrin on 2008-06-01
> **meierfra. said:**
> ??????????  All I know is that Gparted can cause booting problems if you resize Vista. (see [here]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"))
Any other issues?

[http://ubuntuforums.org/showthread.php?t=805273](http://ubuntuforums.org/showthread.php?t=805273)

Need i say more?

---

### Post by SirPerigrin on 2008-06-01
To Further clarify again, on sda6 exist a single installation of 8.04 with both the default installed kernel, and a newer kernel that was downloaded through updates. Each kernel shows up independently on the boot menu, but belong to the same system. Note the different version numbers at the end of the kernel names. The third pair of entrys is your old 7.10 install which should be deleted as it serves no purpose. however you may recover any data you wish by simply mounting the partition (Its likely automounted so just browse your system).

---

### Post by meierfra. on 2008-06-01
> Need i say more? 
Whenever you repartition, there is a chance of data loss (regardless of the program you are using). But I have seen very few cases in  the forum where gparted has caused problems. Personally I have used gparted lots and lots of times without any problems. gparted is widely recommended in the ubuntu forum for all your partitioning (except for resizing Vista partitions)

---

### Post by CPlusPunk on 2008-06-01
Thank you, Thank you..
I did as you recommended and the 7.10 version was removed from the boot up selection. I will take your advise and not use GParted to repartition the harddrive. I understand it is not safe and I have not been at this long enough to feel comfortable doing that. But, once again I would really like to thank you for your help. Have a good evening.

---

### Post by meierfra. on 2008-06-01
If you want to play it save, don't resize your Ubuntu partition. But I still would recommend that you use gparted (or whatever program you prefer) to reformat /dev/sda3 and use it as a Data or Home partition. No reason to waste all that hard disk space. Reformating only takes a few seconds and is very low risk.  You don't have to do it  now, just keep it in mind.

---

### Post by SirPerigrin on 2008-06-02
> **meierfra. said:**
> If you want to play it save, don't resize your Ubuntu partition. But I still would recommend that you use gparted (or whatever program you prefer) to reformat /dev/sda3 and use it as a Data or Home partition. No reason to waste all that hard disk space. Reformating only takes a few seconds and is very low risk.  You don't have to do it  now, just keep it in mind.

I concur, and its exactly what i recomended doing earlier. Its very safe to do this kind of partitioning with GParted, even a windows98 boot floppy can get that right. Its the resizing where GParted puts you at risk.

Refer back to my earlier post for instructions on what drives to delete

---

### Post by CPlusPunk on 2008-06-02
Someone from my IT department got me started on Ubuntu, I will have them help me with the partitioning.

---

### Post by meierfra. on 2008-06-02
> to delete /dev/sda3 and /dev/sda5

I just would like to point out a couple of complication with deleting /dev/sda5

1.  If you delete /dev/sda5, then the partition numbers will change. Namely your ubuntu partition /dev/sda6 will become /dev/sda5. As a consequence you will have to reinstall grub and edit "menu.lst". 

2.  You won't be able to delete /dev/sda5  while running gparted from  Ubuntu. All partitions after /dev/sda5 need to be unmounted, but you won't be able to unmount  the Ubuntu partition /dev/sda6. 

These  problems will not arise when you delete /dev/sda3, since /dev/sda3 is a primary partition. They  also won't arise for /dev/sda7, since it comes after /dev/sda6.

---

