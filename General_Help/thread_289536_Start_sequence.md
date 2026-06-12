---
title: "Start sequence"
date: 2006-10-31
forum: General Help
---

### Post by MacPC on 2006-10-31
Hi,

Currently, my PC is set up for triple boot. Windows 2000 Pro, Windows XP Pro and Ubuntu.

I am just wondering if I can simplify the boot up sequence.

Right now, when I boot up, the Grub comes up first, it will automatically boot into Ubuntu if I don't take any action. If I choose to boot up in Windows, the the Windows boot.ini will ask me to choose between 2000 or XP.

What I like to do is have one page give me the list of three choices like
Windows 2000
Windows XP
Linux

I try to modified the boot.ini, added  C:\ Linux = "Linux" as one item after Windows, but when I choose Linux, it will take me back to the Grub.

Do I need to eliminate Grub all together? How?
Do I need to get rid of boot.ini and modify the Grub? How?

Thanks in advance.

MacPC

---

### Post by elpuerco on 2006-10-31
I think the grub deals with this?  It does for me and by editing the file /boot/grub/menu.lst you can change the load sequence.

---

### Post by jazzgossen on 2006-10-31
Yes, I think getting rid of boot.ini and configuring GRUB will be the easiest way. In order to find out how to modify GRUB's menu.lst, have a look at the output of "sudo fdisk -l". There you can find the partition where Win2k is installed. Then you can hopefully copy the current Windows entry in menu.lst and modify it to match you Win2k partition instead of the XP one. If not, please post the output of the fdisk command, and your current menu.lst.

---

### Post by MacPC on 2006-10-31
Thanks Jazz, The fdisk output looks like this:

   Device Boot     Start            End          Blocks           Id        System
/dev/hda1           *              6949       55817811        7     HPFS/NTFS
/dev/hda2         6950         9728       22322317+      f      W95 Ext'd (LBA)
/dev/hda5         6950         8339       11165143+      7     HPFS/NTFS
/dev/hda6         8340         9473         9108823+     83    Linux
/dev/hda7         9474         9728         2048256       82     Linux swap/Solaris


But I am not quit sure how to get the menu.lst. Is this a file in Windows or in Ubuntu? 


MacPC

---

### Post by MacPC on 2006-10-31
Silly me, I found menu.lst. Can't you tell I am a Linux newie?

---

### Post by jazzgossen on 2006-10-31
Good. It's not always easy to find stuff in Linux if you're not used to it. The "locate" command is good to know, though.

What I would do next is to copy the block in menu.lst that has to do with Windows XP, change the title of the copied block to "Windows 2000" or whatever, and change the "root" directive. If XP is installed on /dev/hda1, I guess that you currently have a line that says "root (hd0,0)". If Win2k is on /dev/hda5, change that to hd(0,4) instead.

Oh, nd make sure to make a backup copy of menu.lst first, in case something goes wrong.

---

### Post by MacPC on 2006-10-31
Thanks. I will do it at my home machine so that I don't screw up the work machine. :)  I will post back one way or the othwr.

MacPC.

---

### Post by MacPC on 2006-11-01
Hi, this is the entire menu.lst on my Ubuntu installation. I am not sure what to do with it.


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
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda6 ro

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
[COLOR="red"]
title		Windows 2000 (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1[/COLOR]

[COLOR="Black"]Is this what you mean?
[/COLOR]

Perhaps I did something wrong, because when I boot to Win 2000, I still get the boot.ini come up to choose between 2000 and XP, but if I try to boot to XP then it won't start.

MacPC

---

### Post by MacPC on 2006-11-01
Oops, somehow the smilies show up at the beginning of the file unintentionally :p

---

