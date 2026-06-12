---
title: "[SOLVED] Linux installed,ok,but what about windows?"
date: 2007-08-29
forum: General Help
---

### Post by bogdan_5844 on 2007-08-29
hi,i am new to the forum,so please someone move/delete this thread if is not in the correct place :)

so,here's my problem: 
I have a PackardBell EasyNote laptop,wich,in it's initial configuration,has 2 partitions:
1 of 10 GB-PackardBell EasyRecovery Partition-Contains a image of the sistem as it was when installed and the Windows Recovery Environment
1 of 150 GB-Windows Vista
I split the second partition,in 2:
Windows Vista- 50GB
Ubuntu Linux 7.04 - 100GB i think(i'm not really sure these are the exact dimensions :P )
anyway,in GRUB,if i select Windows Vista/Longhorn Loader(i wanted to keep it for gaming)it loads the recovery partition loader,not the OS itself,wich takes me to WinRE.How can I fix this?:confused: Thanks in advance ;)

---

### Post by lisati on 2007-08-29
To be honest, I don't know the complete answer but have a thought: Do you have more than one menu item for Windows on your menu?

(When I installed Ubuntu on my desktop (one by Compaq) I left the XP recovery partition intact, and shrunk the main XP partition. When I boot, I have two entries for XP in the Grub menu - choosing the first starts the Windows recovery, choosing the second starts XP - do you have such an option?

---

### Post by bogdan_5844 on 2007-08-29
nope,i have only one entry,wich leads me to WinRE :(

---

### Post by forestpixie on 2007-08-29
can you post the output of this (open aterminal and enter)

```
sudo fdisk -l
```

then in terminal enter this and post it as well

```

cat /boot/grub/menu.lst
```

---

### Post by bogdan_5844 on 2007-08-29
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8388608   27  Unknown
/dev/sda2            1045       12892    95160320    7  HPFS/NTFS
/dev/sda3           12893       19183    50532457+  83  Linux
/dev/sda4           19184       19457     2200905    5  Extended
/dev/sda5           19184       19457     2200873+  82  Linux swap / Solaris

that's the output from fdisk
> 
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
# kopt=root=UUID=9566a946-68fb-4692-a325-fc86dd462b11 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=9566a946-68fb-4692-a325-fc86dd462b11 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=9566a946-68fb-4692-a325-fc86dd462b11 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9566a946-68fb-4692-a325-fc86dd462b11 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9566a946-68fb-4692-a325-fc86dd462b11 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive

and that is my menu.lst :)

---

### Post by forestpixie on 2007-08-29
Ok, it looks like grub is pointing at the recovery partition- we can try to change it to point at the right partition.

backup the menu.lst first - in a terminal

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.2908
```

then open it for editing

```
gksudo gedit /boot/grub/menu.lst
```


go to the end of the file and change the (hd0,0) to (hd0,1)


> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root [COLOR="Red"](hd0,1)[/COLOR]
savedefault
makeactive

save and close

as an aside if you're pasting something long like menu.lst instead of using quote to put it in a box use code (it's the # symbol)

---

### Post by forestpixie on 2007-08-29
re - you're exaile thread to mark a thread solved - use thread tools on the first post and 'mark as solved' is an option - it changes the title for you :)

---

### Post by bogdan_5844 on 2007-08-29
it WORKS! \\:D/ Posting from Vista Home Premium right now,thank you very very much,you are the man,forestpixie!  =D> i marked as solved the exaile thread ;)

---

### Post by forestpixie on 2007-08-29
cracking - glad I could help with this - exaile is now bugging me :D

---

