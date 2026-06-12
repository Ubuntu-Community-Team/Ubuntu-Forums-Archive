---
title: "SATA drives"
date: 2007-09-02
forum: General Help
---

### Post by rspaulding on 2007-09-02
Hi there, I need some help getting Ubuntu to see my SATA drives.

I have 1 IDE drive which is partitioned (1 partition for Ubuntu, and the other half for Windows)
I have sucessfully been able to dual boot with the help of Super Grub Disk, but when I boot into Ubuntu the SATA drives are not listed in Nautilus.  However, in Windows the drives are listed in the Explorer, but when I try to open them, it wants me to format the drives which I won't do because I'm trying to obtain data off of them.

What do I have to do to get into these drives?
thanks

---

### Post by taekwondodogoof on 2007-09-02
I don't know if you've tried this but try installing ntfs-3g.
```
sudo apt-get install ntfs-3g
```

---

### Post by rspaulding on 2007-09-02
> **taekwondodogoof said:**
> I don't know if you've tried this but try installing ntfs-3g.
```
sudo apt-get install ntfs-3g
```
I'm sorry, I am very new to Ubuntu and i'm afraid i don't exactly know what this means.  What is NTSFS-3g? What does it do? and i assume that code is something you type in the terminal?

---

### Post by rspaulding on 2007-09-02
If this helps, here are the results to:
```
sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9732    78172258+   7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326    7  HPFS/NTFS

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       10011    80413326    7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5099    40957686   83  Linux
/dev/hda2   *        5100       19082   112318447+   7  HPFS/NTFS
/dev/hda3           19083       19457     3012187+   5  Extended
/dev/hda5           19083       19457     3012156   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+   7  HPFS/NTFS

---

### Post by rspaulding on 2007-09-03
anyone?
:confused:

---

### Post by logos34 on 2007-09-03
You would type this in a terminal (just like you did for fdisk):

**sudo apt-get install ntfs-config**

It'll fetch all the dependencies as well as ntfs-3g.  You then run

ntfs-config

and enable write support. 

But before you do this post your **/etc/fstab** file.  At the very least you should be able to mount those ntfs partitions read-only.

You shouldn't have to use the SuperGrub cd to boot.  Post your **/boot/grub/menu.lst** file too.  Could be an error somewhere. What is the **hard disk** boot order in the BIOS?  
(Looks like hda should be first.)

In windows, right-click on these sata drives>Properties>tools>**error-checking/chkdsk** with repair option.

---

### Post by rspaulding on 2007-09-03
> **logos34 said:**
> But before you do this post your **/etc/fstab** file....
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9c158c8f-0f05-45df-b0ae-1c5d91e18382 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=29bffcc3-6574-4315-927a-bfc14a3a11e9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

> **logos34 said:**
> You shouldn't have to use the SuperGrub cd to boot.  Post your **/boot/grub/menu.lst** file too.
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
# kopt=root=UUID=9c158c8f-0f05-45df-b0ae-1c5d91e18382 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9c158c8f-0f05-45df-b0ae-1c5d91e18382 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9c158c8f-0f05-45df-b0ae-1c5d91e18382 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9c158c8f-0f05-45df-b0ae-1c5d91e18382 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9c158c8f-0f05-45df-b0ae-1c5d91e18382 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

> **logos34 said:**
> In windows, right-click on these sata drives>Properties>tools>**error-checking/chkdsk** with repair option.
I did this and when i click "start" to run the error checking, the box just closes and nothing happens.

---

### Post by stinger30au on 2007-09-03
try this
[http://ubuntuforums.org/showthread.php?t=529838](http://ubuntuforums.org/showthread.php?t=529838)

---

### Post by logos34 on 2007-09-03
> **rspaulding said:**
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

See that?  The hiddenmenu option is enabled.  No wonder you're using SuperGrub.  You need to hit the Esc key as soon as you see 'Grub loading...' to bring up the menu.  Or comment it out like this

**[COLOR="Red"]#[/COLOR]**hiddenmenu


and the grub menu screen will appear at boot, giving you a choice of OSs.

For the sata mount issue, you can use that psydm gui thingy that the above poster suggested (I have it installed too), but it's not very hard to add entries to fstab so they automount at startup. 

Try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

All you need to do is create a few mount points in /media, then add some lines like this to fstab:

**/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0**
OR 
**/dev/sda1 /media/sda1 ntfs nls=utf8,umask=0222 0 0**

Then, 

**sudo mount -a**

If and when you can mount and read your files, try adding write support with ntfs-3g.
  
But none of this may work if windows won't let you access or do anything to those drives:
> when i click "start" to run the error checking, the box just closes and nothing happens.

You might try checking the Bios to make sure that detect is set for '[auto]', not [user]...Or try TestDisk to fix any errors in the parition tables or drive geometry.

---

