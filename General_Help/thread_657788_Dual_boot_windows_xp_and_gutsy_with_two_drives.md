---
title: "Dual boot windows xp and gutsy with two drives"
date: 2008-01-03
forum: General Help
---

### Post by Wangfu on 2008-01-03
So I have this problem with dual booting my machine right now. I used to have no problem dual booting through grub but after i got back from a trip my menu.lst changed back to the default which I'll post below after I updated ubuntu. Anyway I've tried adding all of the stuff that I've seen around the web to menu.lst involving dual booting and none of it seems to work.

Also when I add that stuff it doesn't even show up in the GRUB menu when I want to choose what I want to boot.

Here's the output of my fdisk -l

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a651a64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72faa21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1824    14651248+  83  Linux
/dev/sdb2            1825        2575     6032407+  82  Linux swap / Solaris
/dev/sdb3            2576       48641   370025145    7  HPFS/NTFS

```

and this is my menu.lst as of this moment (which I know doesn't have any target for the MBR for XP)

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
# kopt=root=UUID=89c45f9e-8d9d-41fe-872a-22e8f52cf822 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=89c45f9e-8d9d-41fe-872a-22e8f52cf822 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=89c45f9e-8d9d-41fe-872a-22e8f52cf822 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I thought it was kind of strange that ubuntu was on hd0 when fdisk says my ubuntu install is on sdb and my xp install is on sda. However it doesn't really matter at the moment cause no matter what i add windows doesn't show up.

I have no idea what to do since I am still just trying to learn Linux. Any and all help is much appreciated, Thanks.

---

### Post by Wangfu on 2008-01-03
Wow so i added this after the ### END DEBIAN AUTOMAGIC KERNELS LIST 

title Windows XP Pro
root (hd1,0)
makeactive
chainloader +1

and i can see windows xp pro on the boot meny but I'm sure i'm doing something wrong because it freezes at the screen where it says

Starting Up...

---

### Post by Wangfu on 2008-01-04
Ok so I really should have tried everything before I posted this but whatever. I got windows to boot and everthing seems to be running fine when I added the lines 

map (hd0) (hd1)
map (hd1) (hd0)

to

title Windows XP Pro
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

It didn't make sense because my windows drive was clearly sda and my linux drive was sdb in fdisk. I thought that meant that the windows drive should be hd0 and the linux drive should be hd,1 but whatever it works.

:popcorn:

---

