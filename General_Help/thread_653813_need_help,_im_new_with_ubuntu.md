---
title: "need help, im new with ubuntu"
date: 2007-12-30
forum: General Help
---

### Post by wacko1jr on 2007-12-30
to anyone who can help me i am having a problem with my computer. i have dual boot on my laptop with vista and ubuntu 7.10. i went into my terminal to try and pull up my grub options so that i could make another pc identical to it. and now when i turn my computer on i can only access ubuntu, ubuntu recovery, and some kind of automatic system check, and my windows vista is not to be found. could someone help me find the other half of my computer please?

---

### Post by taurus on 2007-12-30
Did you make a backup copy of your menu.lst before you started editing it?  What's the output of this command from a terminal?

```
sudo ls -la /boot/grub
```

---

### Post by wacko1jr on 2007-12-30
no, i didnt make a back up, i really didnt think that i had done anything, and im sorry i am new at this, what are you asking me for when you say output

---

### Post by taurus on 2007-12-30
Run that command from a terminal and post the output here.

---

### Post by wacko1jr on 2007-12-30
here you go sir.

kenny@kenny-laptop:~$ sudo ls - la /boot/grub
[sudo] password for kenny:
ls: -: No such file or directory
ls: la: No such file or directory
/boot/grub:
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
kenny@kenny-laptop:~$

---

### Post by taurus on 2007-12-30
There should be a space between - and l.

```
sudo ls -la /boot/grub
```
However, do you see the menu.lst~?  That is your original file.  When you invoke gedit, it would automatically make a backup for your with the ~ at the end.  So, if you want to use the original file, run

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bad
sudo cp /boot/grub/menu.lst~ /boot/grub/menu.lst
```
Reboot and you should get your original GRUB menu back.

---

### Post by wacko1jr on 2007-12-30
after i ran this, sudo ls -la /boot/grub/menu.lst. this is what i got:

kenny@kenny-laptop:~$ sudo ls - la /boot/grub/menu.lst 
ls: -: No such file or directory
ls: la: No such file or directory
/boot/grub/menu.lst
kenny@kenny-laptop:~$ 

what should i do now???

oh and i also tried rebooting and it still didn't show my vista

---

### Post by taurus on 2007-12-30
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bad
sudo cp /boot/grub/menu.lst~ /boot/grub/menu.lst

```

---

### Post by wacko1jr on 2007-12-30
do i type those in at the same time

---

### Post by oldos2er on 2007-12-30
One at a time.

---

### Post by wacko1jr on 2007-12-30
this is what happened

kenny@kenny-laptop:~$ sudo ls - la /boot/grub/menu.lst 
ls: -: No such file or directory
ls: la: No such file or directory
/boot/grub/menu.lst
kenny@kenny-laptop:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bad
[sudo] password for kenny:
kenny@kenny-laptop:~$ sudo cp /boot/grub/menu.lst~ /boot/grub/menu.lst
kenny@kenny-laptop:~$

---

### Post by taurus on 2007-12-30
> **wacko1jr said:**
> this is what happened

kenny@kenny-laptop:~$ sudo ls - la /boot/grub/menu.lst 
ls: -: No such file or directory
ls: la: No such file or directory
/boot/grub/menu.lst
kenny@kenny-laptop:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bad
[sudo] password for kenny:
kenny@kenny-laptop:~$ sudo cp /boot/grub/menu.lst~ /boot/grub/menu.lst
kenny@kenny-laptop:~$

Please, there is no space between the - and the la that you type.

```
sudo ls     -la     /boot/grub
```
Just reboot and see if the old/original GRUB menu appears.

---

### Post by wacko1jr on 2007-12-30
when you show me a command, what i have been doing is a copy and paste into the terminal, i copied the last thing and this is what popped up.

kenny@kenny-laptop:~$ sudo ls     -la     /boot/grub
[sudo] password for kenny:
total 228
drwxr-xr-x 2 root root   4096 2007-12-30 13:55 .
drwxr-xr-x 3 root root   4096 2007-12-22 23:47 ..
-rw-r--r-- 1 root root    197 2007-11-10 20:06 default
-rw-r--r-- 1 root root     15 2007-11-10 20:06 device.map
-rw-r--r-- 1 root root   8660 2007-11-10 20:06 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-11-10 20:06 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-11-10 20:06 installed-version
-rw-r--r-- 1 root root   9152 2007-11-10 20:06 jfs_stage1_5
-rw-r--r-- 1 root root   4773 2007-12-30 14:23 menu.lst
-rw-r--r-- 1 root root   4773 2007-12-22 23:47 menu.lst~
-rw-r--r-- 1 root root   4773 2007-12-30 14:22 menu.lst.bad
-rw-r--r-- 1 root root   7860 2007-11-10 20:06 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-11-10 20:06 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-11-10 20:06 stage1
-rw-r--r-- 1 root root 110292 2007-11-10 20:06 stage2
-rw-r--r-- 1 root root   9980 2007-11-10 20:06 xfs_stage1_5
kenny@kenny-laptop:~$ 

is this the part where i reboot or do i need to do something else?

---

### Post by wacko1jr on 2007-12-30
is there anyone out there???? what is the next step???

---

### Post by taurus on 2007-12-30
Looks to me like both menu.lst~ and menu.lst.bad (the version after you modified it) are the same or at least the same bytes.  What's the output of this command from a terminal?

```
sudo diff /boot/grub/menu.lst~ /boot/grub/menu.lst.bad
```

---

### Post by wacko1jr on 2007-12-30
kenny@kenny-laptop:~$ sudo diff /boot/grub/menu.lst~ /boot/grub/menu.lst.bad
[sudo] password for kenny:
kenny@kenny-laptop:~$

---

### Post by taurus on 2007-12-30
It means they are all the same.  Can you post your /boot/grub/menu.lst then.

```
sudo cat /boot/grub/menu.lst
```

---

### Post by wacko1jr on 2007-12-30
kenny@kenny-laptop:~$ sudo cat /boot/grub/menu.lst
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
# kopt=root=UUID=1f91b1de-f2e0-4d61-8f3d-b885470d8c46 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1f91b1de-f2e0-4d61-8f3d-b885470d8c46 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1f91b1de-f2e0-4d61-8f3d-b885470d8c46 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
##title         Other operating systems:
##root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
##title         Dell Utility Partition
##root          (hd0,0)
##savedefault
##makeactive
##chainloader   +1


## This entry automatically added by the Debian installer for a non-linux OS
## on /dev/sda5
##title         Microsoft Windows XP Embedded
##root          (hd0,4)
##savedefault
##makeactive
##chainloader   +1

kenny@kenny-laptop:~$

---

### Post by taurus on 2007-12-30
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and comment out the last entry, at the bottom, for your XP.

```

## This entry automatically added by the Debian installer for a non-linux OS
## on /dev/sda5
title Microsoft Windows XP Embedded
root (hd0,4)
savedefault
makeactive
chainloader +1

```
Save it and close the gedit window.  Then, reboot and see if you have an entry for your XP and whether you can boot your XP again.

---

### Post by wacko1jr on 2007-12-30
what do you mean comment out, and where do i put what, i just dont want to mess anything else up

---

### Post by taurus on 2007-12-30
Comment out means remove the # in front of the line.  Please look at my previous post since I even showed you what it should look like with an entry for your XP.

You need to make this in /boot/grub/menu.lst

```

## This entry automatically added by the Debian installer for a non-linux OS
## on /dev/sda5
[COLOR="Blue"]##[/COLOR]title Microsoft Windows XP Embedded
[COLOR="Blue"]##[/COLOR]root (hd0,4)
[COLOR="Blue"]##[/COLOR]savedefault
[COLOR="Blue"]##[/COLOR]makeactive
[COLOR="Blue"]##[/COLOR]chainloader +1

```
to look like this.

```

## This entry automatically added by the Debian installer for a non-linux OS
## on /dev/sda5
title Microsoft Windows XP Embedded
root (hd0,4)
savedefault
makeactive
chainloader +1

```

---

### Post by wacko1jr on 2007-12-30
oh hey i just realized something, after i rebooted i tried to access xp, it told me this:

error 12: invalid device request 
press any key to continue...

what i realized was that my second os is vista, not xp

so what would be the next course of action??

---

### Post by taurus on 2007-12-30
Can you post

```
sudo fdisk -l
```
That would be a lower case letter L.

---

### Post by wacko1jr on 2007-12-30
here you go

kenny@kenny-laptop:~$ sudo fdisk -l
[sudo] password for kenny:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       13827   100501504    7  HPFS/NTFS
/dev/sda4           13828       19458    45223616    f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6   *       13828       18908    40813101   83  Linux
/dev/sda7           18909       19130     1783183+  82  Linux swap / Solaris

Partition table entries are not in disk order
kenny@kenny-laptop:~$

---

### Post by taurus on 2007-12-30
Edit your /boot/grub/menu.lst again and make a minor change to the entry at the end.

```

## This entry automatically added by the Debian installer for a non-linux OS
## on /dev/sda5
[COLOR="Blue"]title Microsoft Windows Vista
root (hd0,2)[/COLOR]
savedefault
makeactive
chainloader +1

```
Save it and reboot.

---

### Post by wacko1jr on 2007-12-30
THANK YOU SO MUCH, i can access vista now. thank you for all of you time and help:):):):):):):)

---

