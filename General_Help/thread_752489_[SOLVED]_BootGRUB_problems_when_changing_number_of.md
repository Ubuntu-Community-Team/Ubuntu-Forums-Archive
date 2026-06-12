---
title: "[SOLVED] Boot/GRUB problems when changing number of drives"
date: 2008-04-11
forum: General Help
---

### Post by ksennin on 2008-04-11
I installed ubuntu 7.10 a while back on a system with 3 hard drives, one had win xp, another was a backup disk, and the third I wiped and gave completely to ubuntu.  I have worked with this setup quite well for months, but this past week I tried removing the backup drive, to move it to an external enclosure and decrease the power-expenditure/heat in my pc, and suddenly my pc will not boot.
Grub reported an error 21, which is failing to find a hard drive. I replaced the drive and it booted perfectly.  However, that is worrisome since I like tinkering with my machines and moving drives about as needed (I have over half a dozen in various places).  

( I also noticed the guys who setup the drives seemed to have screwed the jumpers up a bit, which likely accounted for slow boots as it took a while for the system to recognize the drives, and the dvd was never recognize at boot messages, though it did work inside the operating systems, curiously. 
The delay in boots never bothered me before, having many years of Windows experience -ha!). 

Likely the ubuntu setup assigned a later number to my drive (3?) and with one less, it gets renumbered at boot and the grub settings cannot find the original designation.  Grub info cannot be in the removed drive itself as using another one as third allowed a normal boot.

So, is there a way to fix this, editing the drive numbering and grub configuration, so I can allow the backup drive to be removable without huge hassle? 

Thanks beforehand.

---

### Post by ajgreeny on 2008-04-11
Post the output of ```
sudo fdisk -l
``` and also ```
cat /boot/grub/menu.lst
```although we only need to see the menu at the bottom of the latter.  It will probably only need the change from hd2,0 to hd1,0 or possibly similar change to show where the linux kernel is sitting.

---

### Post by ksennin on 2008-04-11
I got this before from sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe884e884

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc733652

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       23968   192522928+  83  Linux
/dev/hdc2           23969       24321     2835472+   5  Extended
/dev/hdc5           23969       24321     2835441   82  Linux swap / Solaris

and cat /boot/grub/menu.lst (which was new to me) gives

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
# kopt=root=UUID=09c29aa9-347e-48aa-9639-73b775821133 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=09c29aa9-347e-48aa-9639-73b775821133 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=09c29aa9-347e-48aa-9639-73b775821133 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by ajgreeny on 2008-04-12
Now using the live CD let's see the output of sudo fdisk -l again.  Or simply try the change I suggested in my first post, change from hd2,0 to hd1,0 in the menu/lst file.  ```
gksudo gedit /boot/grub/menu/lst
``` to do that.

---

### Post by ksennin on 2008-04-15
Thanks, but I tried

gksudo gedit /boot/grub/menu/lst

and it gives me only an empty/blank file, with nothing to edit. Dunno why.

Will try now with the live cd as you said.

---

### Post by logos34 on 2008-04-15
> **ksennin said:**
> Thanks, but I tried

gksudo gedit /boot/grub/menu/lst

and it gives me only an empty/blank file, with nothing to edit. Dunno why.

Will try now with the live cd as you said.

There's a typo.  It should be 

> /boot/grub/menu**[COLOR="Red"].[/COLOR]**lst

If working from the live cd you need to mount the partition first by clicking on it in nautilus file browser.  It should mount at '/media/disk/.'  Then

> gksudo gedit /media/disk/boot/grub/menu.lst

---

### Post by dstew on 2008-04-15
> So, is there a way to fix this, editing the drive numbering and grub configuration, so I can allow the backup drive to be removable without huge hassle?Grub's stage 1 and stage 1.5 bootloaders on the first disk are embedded with a block address that refers to your third disk, so that it can find its stage2 file. When you remove the second disk, the block address becomes wrong, and grub is looking for a non-existent disk.

If you re-arrange your disks, so that the backup disk is the third disk, and re-install grub so that it finds its stage2 on the second disk, then you should be able to remove the backup disk without grub breaking down. To reinstall grub in such a way that it gets its stage2 from the second disk, with its MBR on the first disk, you would issue these commands in the grub shell (from a live CD boot):```
root (hd1,0)
setup (hd0)
quit
```You would also have to edit the menu.lst file to change the #groot value to (hd1,0), and run sudo update-grub to fix the menu item entries.

---

### Post by ksennin on 2008-04-16
> **dstew said:**
> Grub's stage 1 and stage 1.5 bootloaders on the first disk are embedded with a block address that refers to your third disk, so that it can find its stage2 file. When you remove the second disk, the block address becomes wrong, and grub is looking for a non-existent disk.

If you re-arrange your disks, so that the backup disk is the third disk, and re-install grub so that it finds its stage2 on the second disk, then you should be able to remove the backup disk without grub breaking down. To reinstall grub in such a way that it gets its stage2 from the second disk, with its MBR on the first disk, you would issue these commands in the grub shell (from a live CD boot):```
root (hd1,0)
setup (hd0)
quit
```You would also have to edit the menu.lst file to change the #groot value to (hd1,0), and run sudo update-grub to fix the menu item entries.


  How do I access the grub shell?  Must I type a special access string at the terminal?

---

### Post by dstew on 2008-04-16
Boot a live CD, open a terminal and enter```
sudo grub
```That starts the grub shell, with the **grub>** prompt. You enter the commands on the grub shell command line.

---

### Post by ksennin on 2008-04-16
Thanks. Will try it as soon as I get back to my home pc.

---

### Post by ksennin on 2008-04-19
Well, I tried thru the live cd and for some reason that escapes me, accessing the grub through sudo grub, and doing the changes suggested, yielded no solution.  The grub continued to give the same failure.  

So I noticed I could do command line editing at the very grub startup screen, pressing e, and did so, changing hd2,0 to hd1,0.  But when I went back to the main grub menu, these changes were not saved. Editing it again and pressing b right there allowed a normal boot, but at the next restart the problem reappeared.

So I did the command line edit, b-for-boot, and then, inside the rebooted system, I did sudo gedit /boot/grub/menu.lst and found the (still-unchanged) boot drive designations at the end of the file, and  changed the hd2's to hd1's, saved the changes and THAT finally solved it.

YAY!

Thanks to AJGREENY, LOGOS34 and DSTEW for the help and patience. I had been using 7.10 since last year, and at last I can have a fast boot. Hope others can benefit from my little mix-up.  

JR

---

