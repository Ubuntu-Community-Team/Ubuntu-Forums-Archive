---
title: "Daul boot problem"
date: 2007-05-25
forum: General Help
---

### Post by niyazb on 2007-05-25
Dear all 

I have installed ubuntu 7.04 on a secondary partition after rebooting i cant get to my windows XP !!

i think i didnt load GRUB ......... tried to search for GRUB to install didnt find 

Can anyone help to return my windows XP back on track :(:(:(:(:(

Thanks

---

### Post by gustavoberman on 2007-05-25
can you boot ubuntu now?
if you do, edit /boot/grub/menu.lst and comment hiddenmenu option
also check in there that you have an option to boot winxp

---

### Post by jimbob on 2007-05-25
Post a copy of your /boot/grub/menu.lst file.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by niyazb on 2007-05-25
I can boot to ubuntu normally but i can't boot to XP 
by the way a new to linux if just bear with me and give me some tips on to find and  edit /boot/grub/menu.lst

Thanks

---

### Post by niyazb on 2007-05-25
here is grub/boot/menu.lst

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
# kopt=root=UUID=a30b0ea2-a0de-411f-ad95-666f09f74965 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a30b0ea2-a0de-411f-ad95-666f09f74965 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a30b0ea2-a0de-411f-ad95-666f09f74965 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by jimbob on 2007-05-25
Open a terminal window in Ubuntu and save a backup copy of your menu.lst:

  cd /boot/grub
  sudo cp menu.lst menu.lst.orig
 
Then open the editor of your choice:

  sudo gedit menu.lst
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by gustavoberman on 2007-05-25
you need winxp section to boot
at the end of the menu.lst add this (assuming that winxp is at the first partition of the primary disk):

title           Microsoft Windows XP Professional
root            (hd0,0)
makeactive
chainloader     +1

an then reboot

---

### Post by niyazb on 2007-05-25
didn't work i got the following error

Error 12:
invalid device request 
Press any key to continue 

:(:(:(:(:(:(:(:(

---

### Post by gustavoberman on 2007-05-25
mmm
post the result of this:

cat /proc/partitions

---

### Post by confused57 on 2007-05-25
Open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by niyazb on 2007-05-25
major minor  #blocks  name

   8     0   39070080 sda
   8     1          1 sda1
   8     5   10233373 sda5
   8     6    4104576 sda6
   8     7     979933 sda7




 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        1908    15317977+   f  W95 Ext'd (LBA)
/dev/sda5               2        1275    10233373+   7  HPFS/NTFS
/dev/sda6            1276        1786     4104576   83  Linux
/dev/sda7            1787        1908      979933+  82  Linux swap / Solaris

---

### Post by gustavoberman on 2007-05-25
change that root (hd0,0)  to root (hd0,4)

---

### Post by niyazb on 2007-05-25
i have changed to root to 4 still getting the same message :(:(
I can see my windows partition from ubuntu under sda5

---

### Post by gustavoberman on 2007-05-25
I think that the partition of winxp was changed on installation
so we have to make him think that he is the one at the first partition (he has so many ego, he cannot work without knowing he is the ONE)

change to this (i think it was like this... sorry):

title           Microsoft Windows XP Professional
unhide (hd0,4)
hide (hd0,0)
rootnoverify (hd0,4)
savedefault
makeactive

---

### Post by gustavoberman on 2007-05-25
> **gustavoberman said:**
> 
title           Microsoft Windows XP Professional
unhide (hd0,4)
hide (hd0,0)
rootnoverify (hd0,4)
savedefault
makeactive

I forgot the 
chainloader +1

---

### Post by niyazb on 2007-05-26
no luck with ubuntu after i have  added the unhide, hide and  rootnoverfiy lines to the boot menu i got error 22 no such partition for all OS's

non of OS loaded neither Ubuntu nor Windows ........... 

Am working since morning to recovering my data from windows partition 

 I will be loading the ubuntu again but this time with better planning :-)

Thanks to all how helped me  trying to solve my problem.

---

