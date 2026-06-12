---
title: "Converted partition now Grub wont load"
date: 2008-05-28
forum: General Help
---

### Post by Silpheed2K on 2008-05-28
I was using Norton Partition Magic in windows to resize my NTFS partition so I can make more room for Linux. (10GB more room)
Si it did resize my NTFS partition and then I tried to resize my etx3 with Linux and it didnt so I tried gparted on the Ubuntu Live CD (which is what I'm typing to you on right now)
I was wondering what I can do to rescue my Linux installation and accomplish resizing my Linux partition to 10GB more.
I converted the ext3 partition from a logical partition to a primary partition after I got done resizing my NTFS partition..

and when my computer boots all I get is an Error 22 from Grub..

Any help is greatly appreciated. (and I'm very thankful I have a Live CD to ask for help on)

---

### Post by logos34 on 2008-05-28
> **Silpheed2K said:**
> 
I converted the ext3 partition from a logical partition to a primary partition after I got done resizing my NTFS partition..

and when my computer boots all I get is an Error 22 from Grub..

EDIT: grub is pointing to the old (logical) partition #, I think that's it.  Reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Possibly all that's wrong is that the ubuntu partition(s) changed #'s.  Are you using Hardy or Gutsy or what?

Click on root partition in Nautilus file manager.  It should mount at '/media/disk'

Post the output from these commands:

cat /media/disk/boot/grub/menu.lst

sudo fdisk -l

---

### Post by Silpheed2K on 2008-05-28
I'm using Hardy
and here's the output from

cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=b7517310-9e2c-4648-a5d7-6facde79640b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b7517310-9e2c-4648-a5d7-6facde79640b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b7517310-9e2c-4648-a5d7-6facde79640b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)




savedefault
makeactive
chainloader	+1

```

sudo fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ac01abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28449   228516561    7  HPFS/NTFS
/dev/sda3           29725       30401     5437971   83  Linux

```

---

### Post by logos34 on 2008-05-28
yeah, reinstall grub and edit menu.lst:

> ## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,[COLOR="Red"]2[/COLOR])**

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
**root		(hd0,[COLOR="Red"]2[/COLOR])**
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b7517310-9e2c-4648-a5d7-6facde79640b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
**root		(hd0,[COLOR="Red"]2[/COLOR])**
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b7517310-9e2c-4648-a5d7-6facde79640b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
**root		(hd0,[COLOR="Red"]2[/COLOR])**
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

ADD:

Where's swap? 

Also, I hope the UUID didn't change when you converted it

---

### Post by Silpheed2K on 2008-05-28
> **logos34 said:**
> yeah, reinstall grub and edit menu.lst:



Where;s swap?

How do i go about doing that? (I've only had linux for a month now)
Also how did you know which numbers to edit and put? for future reference

---

### Post by logos34 on 2008-05-28
> **Silpheed2K said:**
> How do i go about doing that?
I gave you the link to reinstall grub(post #2)

To edit menu.lst, open as root:

**sudo gedit **/media/disk/boot/grub/menu.lst
> 
Also how did you know which numbers to edit and put? for future reference

> /dev/sda3           29725       30401     5437971   83  Linux


grub starts counting from 0, so you just subtract 1:

sda1 = hd0,0 (first disk, first partition)

sda3 = hd0,2 (first disk, third partition)


Once you get up and running I encourage you to make a swap partition (use gparted).  Then add a line to fstab

gksudo gedit /etc/fstab

> /dev/sda? none swap sw 0 0

---

### Post by Silpheed2K on 2008-05-28
Thanks that did the trick and I didnt setup a swap partition to begin with but I'll check that out..
(I'm running 2GB of RAM so I wasn't too worried)
Thanks

---

### Post by geo909 on 2008-05-28
[Super grub disk]("http://www.supergrubdisk.org/") is said to make things automagically when it comes to reinstalling grub. Although I haven't used it, I think it's quite popular, so you may want to give it a try...

---

### Post by logos34 on 2008-05-28
> **Silpheed2K said:**
> Thanks that did the trick and I didnt setup a swap partition to begin with but I'll check that out..
(I'm running 2GB of RAM so I wasn't too worried)
Thanks

yeah, if you have that much ram it's not as much of an issue.  

Anyhow, glad it's fixed. enjoy!

---

