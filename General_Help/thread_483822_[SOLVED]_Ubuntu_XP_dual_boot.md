---
title: "[SOLVED] Ubuntu XP dual boot"
date: 2007-06-25
forum: General Help
---

### Post by jmarcellais on 2007-06-25
I had an XP machine that I used Partition Magic to create another Primary Partition on the primary HDD. It set the new Linux partition to active and I was able to install Ubuntu 7.04 successfully. Ubuntu starts up and works great, but now I'm unable to get back into Windows. There no boot screen at startup to select OS. I'm a total Linux n00b, any ideas?

thanx,

Joe

---

### Post by LaRoza on 2007-06-25
What does "/boot/grub/menu.lst" look like? Specifically the entries at the bottom. Paste the document, don't edit yet.

---

### Post by jmarcellais on 2007-06-25
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
# kopt=root=UUID=9f8f4f72-15c6-4fa8-8263-6c577f70cdb8 ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9f8f4f72-15c6-4fa8-8263-6c577f70cdb8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9f8f4f72-15c6-4fa8-8263-6c577f70cdb8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9f8f4f72-15c6-4fa8-8263-6c577f70cdb8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9f8f4f72-15c6-4fa8-8263-6c577f70cdb8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by r0ck80y on 2007-06-25
Just a couple of changes you can make in the file:
1) Replace "timeout  3" with **timeout  10**
2) Add the following lines at the end of the file after "### END DEBIAN AUTOMAGIC KERNELS LIST" :```
[B]
title           Windows 
root            (sd0,0)
savedefault
makeactive
chainloader     +1[/B]

```
NOTE: (sd0,0) means your first hdd and the first partition (sda1). If, say, your windows is on sda2, then you write that as (sd0,1). Make that adjustment accordingly. Save the file and reboot.

---

### Post by DagMan on 2007-06-25
That's not enitirely accurate and doesn't look like it will work.  You'lle want to know which partition your Windows install is on and then for example if you have Ubuntu on the first two primary partitions and Windows on the third primary partition it would look more like this:


title           Windows 
root            (hd0,2)
*savedefault*
makeactive
chainloader     +1

It's hd0 and not sd0.  Also If Ubuntu is on root (hd0,0) then Windows will be on something else.  My Ubuntu is on (hd0,2) and Windows is on (hd0,3)  
I don't know what savedefault does but it's not in my menu.





Enough of the technical looking mumbo jumbo.  If you can go into Ubuntu and just paste here the output of 
```
sudo fdisk -l
```
then we can see where Windows is sitting on your drive.

---

### Post by jmarcellais on 2007-06-25
No matter what changes I make, I'm unable to save them. The save function is grayed out, and when I try to go to save as and overwrite the current copy, it tells me "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by merlinus on 2007-06-25
Try this:

```

gksduo gedit /boot/grub/menu.lst

```

-merlin

---

### Post by jmarcellais on 2007-06-25
Copied command into terminal. getting error: bash: gksduo: command not found.

---

### Post by DagMan on 2007-06-25
It's gksudo.  He mis-spelled it.  sudo will work as well.

---

### Post by southernman on 2007-06-25
> **DagMan said:**
> It's gksudo.  He mis-spelled it.  sudo will work as well.It will work, but when using a gui app like gedit ALWAYS use gksudo.

---

### Post by jmarcellais on 2007-06-25
ok. well. I edited the menu.lst file. Still unable to get Windows to boot. Tried several different HD partition numbers. Getting various errors:

hd0,0 error:13 invalid executable format
hd0,1 error:12 Invalid device request
hd1,0 NTLDR is missing
hd1,1 No partition exists

---

### Post by confused57 on 2007-06-25
> **jmarcellais said:**
> ok. well. I edited the menu.lst file. Still unable to get Windows to boot. Tried several different HD partition numbers. Getting various errors:

hd0,0 error:13 invalid executable format
hd0,1 error:12 Invalid device request
hd1,0 NTLDR is missing
hd1,1 No partition exists
As DagMan suggested, post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by jmarcellais on 2007-06-25
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9324    74894998+  83  Linux
/dev/hda2            9325        9726     3229065    5  Extended
/dev/hda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       48641   390708801   17  Hidden HPFS/NTFS

---

### Post by confused57 on 2007-06-25
> **jmarcellais said:**
> Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9324    74894998+  83  Linux
/dev/hda2            9325        9726     3229065    5  Extended
/dev/hda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       48641   390708801   17  Hidden HPFS/NTFS

In Ubuntu open a terminal(Applications---Accessories---Terminal), enter(copy&paste one line at a time, press "enter" after each line):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

copy & paste this entry to the very end of the menu.lst file:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

quit & save

reboot your computer & see if the Window's entry will boot Windows...

---

### Post by jmarcellais on 2007-06-26
Still getting NTLDR is missing error. I burned a Super Grub disk, trying to see if I could get it to work off of there, still nothing, and now I've lost my 400GB hard drive used for data storage. Was working previously, but now seems to be hidden. Tried to unhide partition and activate partition within Super Grub. Still unable to get to data, although drive still appears in sudo fdisk -l.

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9324    74894998+  83  Linux
/dev/hda2            9325        9726     3229065    5  Extended
/dev/hda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       48641   390708801    7  HPFS/NTFS

---

### Post by confused57 on 2007-06-26
Does Windows boot, if you select to boot your Window's drive first in bios?  If it does, then you know your ntldr isn't actually missing...if this is the case, you might want to see what your device.map shows:
```
gedit /boot/grub/device.map
```

It "should" show hda as (hd0) & hdb as (hd1):
```
(hd0) /dev/hda
(hd1) /dev/hdb
```

You might want to read over this explanation & possible solutions for the error:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#NTLDR_is_missing_press_any_key_to](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#NTLDR_is_missing_press_any_key_to)

---

### Post by jmarcellais on 2007-06-26
Still unable to boot into Windows. Still getting same NTLDR missing error. Followed your link provided and tried to use a FIX NTLDR boot disk. still the same. Also still unable to see slave hard drive. 

device map:
(hd0)	/dev/hda
(hd1)	/dev/hdb

sudo fdisk -l:
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9324    74894998+  83  Linux
/dev/hda2            9325        9726     3229065    5  Extended
/dev/hda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       48641   390708801    7  HPFS/NTFS

---

### Post by logos34 on 2007-06-26
> I had an XP machine that I used Partition Magic to **create another Primary Partition on the primary HDD**. It set the new Linux partition to active and I was able to install Ubuntu 7.04 successfully. Ubuntu starts up and works great, **but now I'm unable to get back into Windows**. There no boot screen at startup to select OS. I'm a total Linux n00b, any ideas?
...

Still getting NTLDR is missing error. I burned a Super Grub disk, trying to see if I could get it to work off of there, still nothing, a**nd now I've lost my 400GB hard drive used for data storage**. Was working previously, but now seems to be hidden. Tried to unhide partition and activate partition within Super Grub. Still unable to get to data, although drive still appears in sudo fdisk -l.

...

**Still unable to boot into Windows.** Still getting same NTLDR missing error. Followed your link provided and tried to use a FIX NTLDR boot disk. still the same. **Also still unable to see slave hard drive**.


There seems to be a misunderstanding here (or I'm missing something--please correct me).  

There is not 'another' primary partition on the 'primary HDD' -- I assume you mean /dev/hda.  There's only one big (ext3 linux) primary partition and a tiny extended parition containing the swap.  You keep referring to 400 GB hdb as the 'data' partition, which appears to be the slave drive to hda on the primary IDE channel...or is it on the secondary channel?  Where is the bootable windows partition (C:\) with NTLDR and the boot files supposed to be?  Because if you originally had windows split into a bootable C: primary partition on disk hda and a D: or E: data partition on disk hdb, you now appear to have only the data partiton on hdb.

---

### Post by logos34 on 2007-06-26
Forgot to ask: 

Did you try to boot directly to the windows drive hdb1, as Confused57 suggested?  Because if that is in fact the bootable windows partition, and NTLDR starts up, then the mbr is ok and the problem is something else. 

Is the NTFS hdb1 mounting in linux, or is there even a mount point for it?  Could you post your fstab?
[B]
cat /etc/fstab[/B]

At the very least you should be able to have read access to it.

---

### Post by kdarkentity on 2007-06-26
Ok well me as being a master of dual boot have one question and one piece of advice... when you used partition magic did you resize your windows partition so that you had the room on your hard drive to install linux? ...because if you resized your windows system thats probably why you cant boot into xp... i in the past have resized my windows partition ...and even with partition magic sometimes this can make your windows system unable to boot... windows simply does not like to be resized... my advice to you is to mount your windows system in linux... copy and save any files and documents that you value and wish to keep... and then format your windows system and reinstall it...

---

### Post by DagMan on 2007-06-26
> **kdarkentity said:**
> Ok well me as being a master of dual boot have one question and one piece of advice... when you used partition magic did you resize your windows partition so that you had the room on your hard drive to install linux? ...because if you resized your windows system thats probably why you cant boot into xp... i in the past have resized my windows partition ...and even with partition magic sometimes this can make your windows system unable to boot... windows simply does not like to be resized... my advice to you is to mount your windows system in linux... copy and save any files and documents that you value and wish to keep... and then format your windows system and reinstall it...

Seems like he can look at the drive contents ands see if NTLDR is there first and if so, make the slave the master and use the Windows disk fixmbr tool before he thinks about reinstalling.  I'm not too familiar with Windows recovery but perhaps even the bootloader can be reinstalled with it.

My first step from here would be seeing if the Windows drive is bootable as a master, as asked by logos, and if not, seeing if it can be repaired as the master... if it can then it should be able to go back as the slave and boot throuogh grub.

---

### Post by jmarcellais on 2007-06-26
> **logos34 said:**
> There seems to be a misunderstanding here (or I'm missing something--please correct me).  

There is not 'another' primary partition on the 'primary HDD' -- I assume you mean /dev/hda.  There's only one big (ext3 linux) primary partition and a tiny extended parition containing the swap.  You keep referring to 400 GB hdb as the 'data' partition, which appears to be the slave drive to hda on the primary IDE channel...or is it on the secondary channel?  **Where is the bootable windows partition (C:\) with NTLDR and the boot files supposed to be?**  Because if you originally had windows split into a bootable C: primary partition on disk hda and a D: or E: data partition on disk hdb, you now appear to have only the data partiton on hdb.

---

Is the NTFS hdb1 mounting in linux, or is there even a mount point for it? Could you post your fstab?

---

when you used partition magic did you resize your windows partition so that you had the room on your hard drive to install linux?

It's suppose to be on /dev/hda1. 

---

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9f8f4f72-15c6-4fa8-8263-6c577f70cdb8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e1d0dc17-3c4f-495a-bf6c-304fbb9e6127 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

Yes, I did resize the Windows partition.

---

### Post by logos34 on 2007-06-26
ok, so try adding an entry for hdb1.

**gksudo gedit /etc/fstab**

add to bottom:

**/dev/hdb1 /media/hdb1 ntfs nls=utf8,umask=0222 0 0**

Save and close.

**sudo mkdir /media/hdb1**

sudo mount -t ntfs /dev/hdb1 /media/hdb1

it should appear on desktop.  If you can access files, reboot.  It should automount on startup.

As for the windows partition on hda that you 'resized' using PM, I don't see it and there's no free disk space left where it might be (all sectors used by linux).  If all your docs and personal files (i.e. My Documents) are on hdb1, then all you'll have to do is reinstall it to hdb drive (shrinking hdb1 and creating a 10gb or so additional partition).

---

### Post by jmarcellais on 2007-06-26
> **logos34 said:**
> ok, so try adding an entry for hdb1.

**gksudo gedit /etc/fstab**

add to bottom:

**/dev/hdb1 /media/hdb1 ntfs nls=utf8,umask=0222 0 0**

Save and close.

**sudo mkdir /media/hdb1**

sudo mount -t ntfs /dev/hdb1 /media/hdb1

it should appear on desktop.  If you can access files, reboot.  It should automount on startup.

As for the windows partition on hda that you 'resized' using PM, I don't see it and there's no free disk space left where it might be (all sectors used by linux).  If all your docs and personal files (i.e. My Documents) are on hdb1, then all you'll have to do is reinstall it to hdb drive (shrinking hdb1 and creating a 10gb or so additional partition).

hdb1 folder appears in the media directory. Does not appear on the dekstop, no files in the folder and free space 63.4GB. When command 
**sudo mount -t ntfs /dev/hdb1 /media/hdb1** is entered, getting error:

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

As for the other problem. I made a backup of my C: drive and Registry settings to the hdb1 before I partitioned and installed Ubuntu, so if I need to blow away the Master (hda1) drive I wont be starting from scratch. I think the problem is that when I resized and activated the new Linux partition on the master drive and installed Ubuntu,  I lost the ability to re-activate the Windows partition. Does this sound plausible?

---

### Post by logos34 on 2007-06-26
okay, try
[B]sudo umount /media/hdb1
sudo mount -t auto /dev/hdb1 /media/hdb1[/B]

---

### Post by jmarcellais on 2007-06-26
> **logos34 said:**
> okay, try
[B]sudo umount /media/hdb1
sudo mount -t auto /dev/hdb1 /media/hdb1[/B]

error: mount: you must specify the filesystem type
also, hdb1 folder still appears in Filesystem/media directory after unmounting with **sudo umount /media/hdb1**

*also see edits to previous post

---

### Post by logos34 on 2007-06-26
sudo mount -t **ntfs** /dev/hdb1 /media/hdb1

(sorry, thought when you put 'auto' it would read it off the fstab.  guess you need to reboot first for that)

---

### Post by jmarcellais on 2007-06-26
> **logos34 said:**
> sudo mount -t **ntfs** /dev/hdb1 /media/hdb1

(sorry, thought when you put 'auto' it would read it off the fstab.  guess you need to reboot first for that)

Still getting same error from 2 posts ago...

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

---

### Post by logos34 on 2007-06-26
hmmm..just reboot.  Hopefully it wil automount hdb1.  If it doesn't try changing the entry in fstab.

**gksudo gedit /etc/fstab**

replace previous entry with:

/dev/hdb1 /media/hdb1 **ntfs defaults,nls=utf8,umask=007,gid=46 0 1**

reboot.

---

### Post by jmarcellais on 2007-06-26
> **logos34 said:**
> hmmm..just reboot.  Hopefully it wil automount hdb1.  If it doesn't try changing the entry in fstab.

**gksudo gedit /etc/fstab**

replace previous entry with:

/dev/hdb1 /media/hdb1 **ntfs defaults,nls=utf8,umask=007,gid=46 0 1**

reboot.

Done and still nothing. I think I'm just gonna go ahead and blow away the hard drive and try to the Ubuntu from the Live CD for now. Thanx to everyone for all the help. This is one of the reasons why I'm interested in Linux, great support from other users. Thanx again.

---

### Post by logos34 on 2007-06-26
> Done and still nothing. I think I'm just gonna go ahead and blow away the hard drive and try to the Ubuntu from the Live CD for now. Thanx to everyone for all the help. This is one of the reasons why I'm interested in Linux, great support from other users. Thanx again.


Sorry to hear that.  You could try one more thing:

**sudo apt-get install ntfs-3g ntfs-config**

This is a driver that is supposed to give you read + write access to NTFS partitions.  If you do

**sudo ntfs-config**

this brings up the gui where you can 'nable write support for internal device.'  It will automatically edit your fstab files.  Maybe after a couple of reboots you will be able to access hdb1.  Or maybe the problem is the mount point.  You could try the (old) /mnt directory.  Maybe the filesystem is damaged in some way, but you'd need a windows install cd to run CHKDSK /r on it.

---

