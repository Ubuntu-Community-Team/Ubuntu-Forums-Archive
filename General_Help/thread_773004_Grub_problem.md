---
title: "Grub problem"
date: 2008-04-28
forum: General Help
---

### Post by daraman2000 on 2008-04-28
I'm dual booting ubuntu 8.04 and windows vista (plz don't flame me :-# ) recently I got a windows game (no, Wine can't do it), so I booted windows. what i got was an engmatic message:
[QUOTE=My Computer]
root		(hd0,1)
savedefault
makeactive
chainloader	+1

GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 
GRUB GRUB GRUB GRUB GRUB GRUB 


[/QUOTE]

and it continued looping "GRUB". reminds me of some common BASIC programs

```
while 1
print "GRUB"
end
```

obviously, Grub isn't written in BASIC. Can anyone help? I'm getting desperate. any other info will be posted on request.

UBERthanks in advanced! :grin:


**EDIT:**
menu.lst ouput posted:
```
gfxmenu /boot/grub/message.suse
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
# kopt=root=/dev/sdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-15-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-15-generic root=/dev/sdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-15-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-15-generic root=/dev/sdb3 ro single
initrd		/boot/initrd.img-2.6.24-15-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-14-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-14-generic root=/dev/sdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-14-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-14-generic root=/dev/sdb3 ro single
initrd		/boot/initrd.img-2.6.24-14-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-12-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-12-generic root=/dev/sdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-12-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-12-generic root=/dev/sdb3 ro single
initrd		/boot/initrd.img-2.6.24-12-generic
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin 
boot

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

```
PS: I'm running Ubuntu, but for some reason update-grub renamed everything...

Fdisk output:
```
dara@MasterFire:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec160575

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       14593   115680256    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bd8a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15506   124545024    7  HPFS/NTFS
/dev/sdb2           15507       17937    19527007+  83  Linux
/dev/sdb3           17938       19153     9767520   83  Linux
/dev/sdb4           19154       19402     2000092+  82  Linux swap / Solaris

```
[URL="http://reviews.cnet.com/laptops/toshiba-satellite-a205-s4639/4507-3121_7-32422061.html"]
My laptop's specs can be found here[/URL]


grub --version yields:
```
dara@MasterFire:~$ sudo grub --version
grub (GNU GRUB 0.97)
```

As you can see, I am running GfxBoot, even though I uninstalled it and reinstalled grub..............

Yes, it works. no, it doesn't boot vista...

Maybe apt- decided to keep gfxBoot?

---

### Post by daraman2000 on 2008-04-28
nobody?

---

### Post by daraman2000 on 2008-04-30
I'm getting desperate! :( sry for double posting,

---

### Post by zoom79 on 2008-05-01
I'm far from an expert (in fact I'm trying to fix my own boot config following an update to HH myself!  :) ), but you might look at some posts dealing with "update-grub".  

In my case, I booted a LiveCD to get online & do the research about how to manually get HH booted, tried it, got in & have used "sudo update-grub" to update my menu.lst.  The next step is to try the reboot & see if it was successful, but I saw your desperation & thought I'd drop a line first (in case I'm NOT successful :(  )

Good Luck!

---

### Post by lswest on 2008-05-01
can you post the output of ```
cat /boot/grub/menu.lst
``` it seems to me something is misconfigured for your vista OS, and the output above the "GRUB"'s may not be all that there is in the file.

---

### Post by bollix47 on 2008-05-01
A search of the web suggests checking your computer's bios settings and see if your hard drives are set to auto detect.

[http://www.linuxquestions.org/questions/ubuntu-63/booting-my-new-ubuntu-install-grub-grub-grub-grub-grub-etc.-518849/](http://www.linuxquestions.org/questions/ubuntu-63/booting-my-new-ubuntu-install-grub-grub-grub-grub-grub-etc.-518849/)

[http://www.trilithium.com/johan/2005/06/grub-grub-grub/](http://www.trilithium.com/johan/2005/06/grub-grub-grub/)

---

### Post by daraman2000 on 2008-05-01
@zoom79
I've already tried GRUB-update; all it did was rename all my Ubuntu entries as Debian. :(

@lswest
I posted the info

@bollix47
I'll try that.



Thanks to all of you for your help! 
Further bulletins will ensue as events warrant!
[SIZE="1"]^calvin & hobbes reference^[/SIZE]

---

### Post by zvacet on 2008-05-02
title		Windows Vista/Longhorn (loader)
rootnoverify		(hd0,1)
makeactive
chainloader	+1

---

### Post by daraman2000 on 2008-05-03
@ zvacet: 
that didn't work....

my BIOS is locked; it seems there's no disable auto detect option....

also, I'm sure it worked b4 i installed gfxboot...

---

### Post by ghost_ryder35 on 2008-05-03
> **daraman2000 said:**
> @ zvacet: 
that didn't work....
 
my BIOS is locked; it seems there's no disable auto detect option....
 
also, I'm sure it worked b4 i installed gfxboot...
have you tried reinstalling grub?  I know it seems dumb to reinstall something that is still there but it just might be what you need.   see my sig :guitar:

---

### Post by lswest on 2008-05-03
try adding this after the "root (hd0, 1)" line by your vista entry in menu.lst
```
map (hd0) (hd1)
map (hd1) (hd0)
```
to edit it do: ```
gksudo gedit /boot/grub/menu.lst
```

---

