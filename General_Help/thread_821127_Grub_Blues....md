---
title: "Grub Blues..."
date: 2008-06-06
forum: General Help
---

### Post by WhitestSand on 2008-06-06
Alright here goes...I have searched high and low, I'm not the greatest at these things but I'm trying. I have installed (3 x's) ubuntu.. and I cant get the OS to open..I have the option  but Error 15: file not found pops up..
Find --set-root-- ignore-floppies/ubuntu/install/boot/grub/menu.1st
I can get to 
GRUB>     if that helps lol

I have tried super grub.. (some of it)
here might be a problem..
I have _I think 0 drive is a 120 gig with a bad xp install,half of it is the ubunto install----
then I have 2 36gig HDs raid with a good xp install..

I have read about trying to find or make sure grub is on the correct partition, my set up is so screwed up Im confused.. If anyone can help I would be grateful .. Please ask pointed questions and I will try to answer them..

I got to run the OS with the cd and I think its cool and cant wait to use it full time..

---

### Post by leito666 on 2008-06-06
could you post 

fdisk -l

---

### Post by damis648 on 2008-06-06
Could you boot up with the live CD, mount your Ubuntu drive (Places>Name/Size of the Drive) browse it, and find boot>grub>menu.lst and copy the contents of that in here? Also, could you give some info on your partition table and you master/slave situation?

---

### Post by WhitestSand on 2008-06-06
Wow That is really the first time I explored inside... here is what you wanted.. is there any way to get the info on the partitions from in here??lol Im sure there is..Ill look around.

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
# kopt=root=UUID=69b16893-3b4b-4e58-a664-fe90af900487 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=69b16893-3b4b-4e58-a664-fe90af900487 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=69b16893-3b4b-4e58-a664-fe90af900487 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by WhitestSand on 2008-06-06
Here is the info on the partitions

/dev/sda    34.47
/dev/sdb    34.47


/dev/sdc   111.79

/dev/sdc1  ntfs   48 gig       boot

/dev/sdc2  extended   62 gig
   /dev/sdc5   ex3
   /dev/sdc6   Linux-Swap


Xp is on a-b  &   c1  ,, kind of sucks

---

### Post by damis648 on 2008-06-06
Interesting... the "File Not Found" Must be referring to the kernel image. Maybe your CD is defective? Did you try different CD's? Burning at slow speeds? Help me out guys.

---

### Post by WhitestSand on 2008-06-07
I burned it three different times.. I even changed sites.. and I had the download program check the cd each time..
could it be looking in the wrong place for the file?
I don't know enough to make an educated guess, I'm always learning something new..
I tried super grub and had it try and fix it for me... but no luck.. even though there seemed to be alot more options I could have tried..

---

### Post by damis648 on 2008-06-07
Try this:

Boot up from the liveCD
Open a terminal and type
```
sudo grub
```
and hit enter.
Now
```
find /boot/grub/stage1
```
and enter.
Note the drive it returns.
Now type
```
root (sdx,x)
```
replacing x with what was returned above. (And/or replacing the sd with hd depending on what was returned.) and press enter.
Finally, type
```
setup (hdx)
```
replacing the x with the number before the comma that we found above. (IE if it was (hd2,3) you would enter setup (hd2).) And enter it.
Now just type
```
quit
```
and enter and close the terminal. This should have reinstalled the GRUB, it however might or might not work.

---

