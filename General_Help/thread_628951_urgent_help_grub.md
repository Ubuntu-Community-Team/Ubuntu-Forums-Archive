---
title: "urgent help grub"
date: 2007-12-01
forum: General Help
---

### Post by paintballer on 2007-12-01
hi,OK im new to Linux.  i installed Ubuntu on my external HD from, my moms computer(bad move) anyways now GRUB is halfway installed on my external HD and on my moms internal HD so my External HD has to be plugged in to access windows or i get error 21. how do i delete GRUB so it boots windows normally pls help my mom is mad. by the way she has a dell if that matters.

---

### Post by Craigus on 2007-12-01
[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console")

---

### Post by meierfra on 2007-12-01
In addition to fixing the MBR you also need to install grub to the MBR of the external drive. (Otherwise you won't be able to boot into ubuntu)

See 
[http://ubuntuforums.org/showthread.php?t=624841]("http://ubuntuforums.org/showthread.php?t=624841")

for a similar case. You might be able to adjust the numbers  yourself. Or   post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

and I can give you detailed instruction.

---

### Post by paintballer on 2007-12-01
thank you, is there anyway i can do this with out an XP cd or if i can download the cd somewhere cause i really don't wanna spend money on buying windows XP if so thanks.

---

### Post by meierfra on 2007-12-01
> is there anyway i can do this with out an XP cd o

The method in my link does not require any CD's.

---

### Post by Craigus on 2007-12-01
[http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html]("http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html")

---

### Post by paintballer on 2007-12-01
sorry im a total noob and im scared you'r going to have to guide me through


***_sudo fdisk -l_***

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9305    74702250    7  HPFS/NTFS
/dev/sda3            9306        9725     3373650   db  CP/M / CTOS / ...

Disk /dev/sdb: 10.0 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f093f08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1164     9349798+  83  Linux
/dev/sdb2            1165        1222      465885    5  Extended
/dev/sdb5            1165        1222      465853+  82  Linux swap / Solaris

***_cat /boot/grub/menu.lst_***

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
# kopt=root=UUID=7393e829-f363-467c-b7bf-f2aff96f0340 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=7393e829-f363-467c-b7bf-f2aff96f0340 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=7393e829-f363-467c-b7bf-f2aff96f0340 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by Craigus on 2007-12-01
I think meierfra's solution will be safer, as Dell often uses a non-standard MBR structure.

---

### Post by paintballer on 2007-12-01
ok thanks. so i need a xp CD or can i use the link you provided with that program?

---

### Post by meierfra on 2007-12-01
Step 1: Fix menu.lst:

Open a terminal (Applications->Accessories->Terminal)

and open the file "menu.lst" via

```
gksudo  gedit  /boot/grub/menu.lst
```

change

"#groot (hd1,0)" to "#groot (hd0,0)"

change:

title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

to


title Microsoft Windows XP Home Edition
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1


Save and close the file. In the terminal:


```
sudo update-grub
```



Step 2: Install Grub to the MBR of the external drive:

```
sudo grub
```

and at the "grub>" prompt

```
root (hd1,0)

setup (hd1)

quit
```


Step 3 Remove grub from the MBR of the internal drive:

If you don't have the "universe" repositories enabled:
Go to Systems-> Adminstration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)
Click on Close (twice)

Next :

```

sudo apt-get update
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda
```

Step 4 Reboot with the external drive first in the boot order in the bios.

---

### Post by paintballer on 2007-12-01
opps sorry nvm misread the names XD ok thanks craig.

---

### Post by paintballer on 2007-12-01
thanks meierfra. i did it but it didnt work but let me try it again so give me 5 mins and ill be back i thiink i saved it after updating grub be back in 5

---

### Post by paintballer on 2007-12-01
i tried it again and in the terminal: im getting error 27 unrecognizable command

---

### Post by meierfra on 2007-12-01
What command where you doing when you got that error?

---

### Post by paintballer on 2007-12-01
sudo apt-get update
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda

---

### Post by meierfra on 2007-12-01
Is your internet    connection  working?

Also you need to hit enter after each line.

---

### Post by paintballer on 2007-12-01
i typed the command in wrong sorry,i retyped it and it worked so let me restart comp brb sorry for the troubles

---

### Post by paintballer on 2007-12-01
lol my mistake i made i know you hear/see this alot but THANKS fixed the problem sorry for my  newbines troubles again thank you very much

---

### Post by meierfra on 2007-12-01
No problem. This actually went fairly smoothly.

---

