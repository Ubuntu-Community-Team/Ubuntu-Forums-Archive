---
title: "Windows XP option not on GRUB boot menu."
date: 2008-06-22
forum: General Help
---

### Post by galvatron1983 on 2008-06-22
Hey guys,

Using Gparted I partitioned my hard drive and created an NTFS partition which Windows XP was installed onto, alongside my current Linux Mint install. 

The problem is, Windows XP is not appearing as an option in the GRUB boot menu, so I cant boot Windows XP if I wished. I know I have to edit the GRUB menu list file, but Im not sure how to do it. 

Heres a screenshot of the partitions on my hard drive. Windows XP is on the NTFS formatted partition. 

[IMG]http://i27.tinypic.com/2r5uql3.jpg[/IMG]

Any help you guys could provide would be great and thanks in advance!

---

### Post by fooman on 2008-06-22
open a terminal and type (or copy/paste):

```
gksudo gedit /boot/grub/menu.lst
```

when it opens,  add the following to the bottom of the file:

```
title           Windows XP 
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

so it looks similar to this:

```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a5b2a33f-53a2-4a98-88ba-3644e6bb1db0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a5b2a33f-53a2-4a98-88ba-3644e6bb1db0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
[COLOR="Blue"]
title           Windows XP 
root            (hd0,1)
savedefault
makeactive
chainloader     +1
[/COLOR]
### END DEBIAN AUTOMAGIC KERNELS LIST
```

save the changes, close the file and reboot.  see if that works.

---

### Post by meierfra. on 2008-06-22
The windows item needs to be BELOW the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise it will disappear after  the next Ubuntu kernel update.

---

### Post by LBattis on 2008-06-22
I hope I'm in the right place to add this question.  If not pls let me know where it would be more appropriate to post.

I've lost the entry in my Boot Menu for launching Windows XP.  The menu worked perfectly until yesterday.  Now the XP entry has disappeared.  When I hilight, "Other Operating Systems:" I get an error message about an entry being unrecognizable.  I can get exact verbiage if it will help.

Here are the applicable parameters from my AMD64 system running 64-bit Ubuntu:

FDISK:

DEVICE      BOOT  START    END      BLOCKS      ID   SYSTEM

/dev/sda1    *    1        3891     31254426    7    HPFS/NTFS
/dev/sda2         3892     36187    259417620   83   Linux
/dev/sda3         38086    38913    6650910     5    Extended
/dev/sda4         36188    38085    15245685    83   Linux
/dev/sda5         38175    38913    5935986     82   Linux Swap/Solaris
/dev/sda6         38086    38174    714829+     82   Linux Swap/Solaris


BOOT MENU:

Ubuntu  8.04,  kernel  2.6.24-19  generic
Ubuntu  8.04,  kernel  2.6.24-19  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-18  generic
Ubuntu  8.04,  kernel  2.6.24-18  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-17  generic
Ubuntu  8.04,  kernel  2.6.24-17  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-16  generic
Ubuntu  8.04,  kernel  2.6.24-16  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-14  generic
Ubuntu  8.04,  kernel  2.6.24-14  generic  (recovery mode)
Ubuntu  8.04,  memtest86+
Other Operating Systems:


/boot/grub/menu.lst:


FDISK:

DEVICE      BOOT  START    END      BLOCKS      ID   SYSTEM

/dev/sda1    *    1        3891     31254426    7    HPFS/NTFS
/dev/sda2         3892     36187    259417620   83   Linux
/dev/sda3         38086    38913    6650910     5    Extended
/dev/sda4         36188    38085    15245685    83   Linux
/dev/sda5         38175    38913    5935986     82   Linux Swap/Solaris
/dev/sda6         38086    38174    714829+     82   Linux Swap/Solaris


BOOT MENU:

Ubuntu  8.04,  kernel  2.6.24-19  generic
Ubuntu  8.04,  kernel  2.6.24-19  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-18  generic
Ubuntu  8.04,  kernel  2.6.24-18  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-17  generic
Ubuntu  8.04,  kernel  2.6.24-17  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-16  generic
Ubuntu  8.04,  kernel  2.6.24-16  generic  (recovery mode)
Ubuntu  8.04,  kernel  2.6.24-14  generic
Ubuntu  8.04,  kernel  2.6.24-14  generic  (recovery mode)
Ubuntu  8.04,  memtest86+
Other Operating Systems:


/boot/grub/menu.lst:

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
# kopt=root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=47fc17dc-57fc-4c7a-9635-075445cf8fcb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=544e3604-75af-40e8-86d4-8589c2e19749 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=544e3604-75af-40e8-86d4-8589c2e19749 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=544e3604-75af-40e8-86d4-8589c2e19749 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=544e3604-75af-40e8-86d4-8589c2e19749 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


. . . 

Any Ideas?

P.S.  Please excuse the smiley faces at the beginning of the, "menu.lst," listing.  They appear to be auto-generated escape code characters.

---

### Post by fooman on 2008-06-22
> **meierfra. said:**
> The windows item needs to be BELOW the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise it will disappear after  the next Ubuntu kernel update.

thanks meierfra!  :)

---

