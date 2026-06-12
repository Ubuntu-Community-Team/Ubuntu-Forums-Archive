---
title: "Problems after partition editing"
date: 2006-10-12
forum: General Help
---

### Post by TaterSalad on 2006-10-12
Hello,

I did some partition editing today. Before my doings, my setup was like this:

My laptop hard drive:

/dev/hda1: primary - ntfs (Windows XP) 
/dev/hda2: primary - ext3 (Ubuntu Home files)
/dev/hda3: primary - linux-swap
/dev/hda4: primary - ext 3 (Ubuntu kernal / system files / etc)

I was going to install another OS on this drive. I needed to make another primary partition. Unfortunately, you can only have four primary partitions on a drive. So... I used a gparted live cd to copy my 3 linux partitions to a usb hard drive. Then I deleted the primary partitions. I then created 2 partitions. One primary for the new OS, and another extended partition. I copied my 3 linux partitions into this extended partition.

My hard drive now looks like this:

/dev/hda1: primary - ntfs (Windows XP) 
/dev/hda2: extended
/dev/hda3: primary - fat32 (New OS)
/dev/hda5: logical - ext 3 (Ubuntu Home files)
/dev/hda6: logical - linux-swap
/dev/hda7: logical - ext 3 (Ubuntu kernal / system files / etc)

After some fidling with GRUB, I got ubuntu to boot. (XP works fine) However, I get the following errors on start up:

*Checking all file systems...
dosfsck 2.11, 12 Mar 2005, fat32, LFN
open /dev/sda1:No such file or directory
fsck.ext 3:Attempt to read block from file system resulted in short read while trying to open /dev/hda2
Could this be a zero length partition? 
*File system check failed. Please repair manually.

I Ctrl-D to keep booting. Then the log on screen comes up. This is as far as I can get though. I cannot log in to GNOME. (regular session or failsafe) I can get to a terminal though.

Any ideas?

Thanks!

---

### Post by TaterSalad on 2006-10-13
Anyone? I might try reverting my home directory to a primary partition to see if that might work.

---

### Post by eniel on 2006-10-13
Did you edit your /etc/fstab file to mount your new partitions in the correct way?
You now have to mount /dev/hda6 as swap and /dev/hda5 as home
so I guess you have to change 
hda2 to hda5
hda3 to hda6
hda4 to hda7

/dev/sda1 is probably your usb stick
/dev/hda2 is the extended partition and should not be mounted

---

### Post by galileon on 2006-10-13
no, your problem is probably in your /etc/fstab

try to boot on a ubuntu live cd, open a terminal, type the follwing:

sudo mkdir /mnt/ubunturoot
sudo mount /dev/hda7 /mnt/ubunturoot
sudo gedit /mnt/ubunturoot/etc/fstab


then replace the partition names as eniel just said...

---

### Post by TaterSalad on 2006-10-14
I think I fixed my fstab. However I have a different problem now.  I run in recovery mode and these are the last few lines:

```
Begin: Running /scripts/local-premount...
Attempting manual resume
attempt to access beyond end of device
hda3: rw=16, want=8, limit=2
Kernal Panic - not syncing: I/O error reading memory image

```

Then it just freezes there. hda3 is my extended partition, so i guess thats why its getting an I/O error. I just dont know what to do.

Thanks!

/dev/hda1: primary - ntfs (Windows XP)
/dev/hda2: primary - hfs+ (Mac OSX)
/dev/hda3: extended
/dev/hda5: logical - ext 3 (Ubuntu Home files)
/dev/hda6: logical - linux-swap
/dev/hda7: logical - ext 3 (Ubuntu kernal / system files / etc)

---

### Post by TaterSalad on 2006-10-15
Is there any where else where I would need to change anything from accessing hda3?

---

### Post by galileon on 2006-10-15
comment it out from fstab if its still there, #

or is it trying to load it as root? if so, the command is in /boot/grub/menu.lst

so again, as above, 


boot on a ubuntu live cd, open a terminal, type the follwing:

sudo mkdir /mnt/ubunturoot
sudo mount /dev/hda7 /mnt/ubunturoot
sudo gedit /mnt/ubunturoot/boot/grub/menu.lst

look for the entry you usually use to boot, it might have something like this (thats mine anyway):

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot


what you want to make sure is that the line kernel........root=/dev/hdaX is really hdaX is hda7 for your own system...

---

### Post by TaterSalad on 2006-10-15
Grub isnt the problem. Its ubuntu. I see the ubuntu splash screen. It just freezes when setting up the file system. The error above is what i get when loading in recovery mode.

---

### Post by eniel on 2006-10-15
In your first post you said that /dev/hda2 is your extended partition
now you say /dev/hda3 is your extended partition
Are you sure your fstab is correct?

---

### Post by TaterSalad on 2006-10-15
Yeah. I redid everything. Thats just how it ended up this time. Guess I should have mentioned that. But I am pretty sure fstab is correct. Is there anything I need to edit that involves setting up the files system?

This is my current setup:

/dev/hda1: primary - ntfs (Windows XP)
/dev/hda2: primary - hfs+ (Mac OSX)
/dev/hda3: extended
/dev/hda5: logical - ext 3 (Ubuntu Home files)
/dev/hda6: logical - linux-swap
/dev/hda7: logical - ext 3 (Ubuntu kernal / system files / etc)

---

### Post by galileon on 2006-10-15
are you sure you checked the grub?

because it is possible to load the kernel and the splash screen, and yet fail to mount the root filesystem if the wrong entry is in grub...sorry if you have already checked...

---

### Post by TaterSalad on 2006-10-15
Hope this clears things up.

Here is the contents of my grub menu.lst:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Mac OS X Tiger 10.4.7
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

Is it possible that Grub is looking for the kernel (/boot/vmlinuz-2.6.15-27-386) in the wrong place?

Here is the contents of my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs-3g    defaults,locale=en_US.utf8 0 0
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

And here is my current partition setup:

```
/dev/hda1: primary - ntfs (Windows XP)
/dev/hda2: primary - hfs+ (Mac OSX)
/dev/hda3: extended
/dev/hda5: logical - ext 3 (Ubuntu Home files)
/dev/hda6: logical - linux-swap
/dev/hda7: logical - ext 3 (Ubuntu kernal / system files / etc)
```


My problem:

Ubuntu freezes at bootup. I see the splash screen, but it never gets past 'Setting up file system'. I launched Ubuntu in recovery mode and these are the last few lines:

```

Begin: Running /scripts/local-premount...
Attempting manual resume
attempt to access beyond end of device
hda3: rw=16, want=8, limit=2
Kernal Panic - not syncing: I/O error reading memory image
```

hda3 is an extended partition and it shouldn't be trying to read there right? So what do I need to do to point it in the right direction?

---

### Post by galileon on 2006-10-15
your grub conf is good, sorry for asking about that again,

/script/local-premount is a folder containing startup scripts stored in your initrd once the kernel loads... the place from which it is read before initrd is built is /etc/mkinitramfs/scripts/local-premount/

mine is empty, could you do a ls /etc/mkinitramfs/scripts/local-premount/

and tell us if there's any scripts there?

---

### Post by TaterSalad on 2006-10-15
Nothing in there.

---

### Post by galileon on 2006-10-15
could you try a different kernel? eg install the same-as-you-got-686 instead of -386... just a thought...

(its in synaptic)

---

### Post by TaterSalad on 2006-10-16
How would I got about that?

---

### Post by galileon on 2006-10-16
are you on a live cd?

if so, download the following (its not a -686, but its a slightly older kernel), save it in the home directory

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.15%2Flinux-image-2.6.15-26-386_2.6.15-26.47_i386.deb&md5sum=87e656c47a9cc80374c289958ec5d13e&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.15%2Flinux-image-2.6.15-26-386_2.6.15-26.47_i386.deb&md5sum=87e656c47a9cc80374c289958ec5d13e&arch=i386&type=security)

open a terminal,

sudo mkdir /mnt/ubunturoot
sudo mount /dev/hda7 /mnt/ubunturoot
sudo dpkg --extract linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb ./linux

sudo cp ./linux/boot/* /mnt/ubunturoot/boot/
sudo cp ./lib/modules/2.6.15-26-386 /lib/modules/ -r

sudo gedit /mnt/ubunturoot/boot/grub/menu.lst


add the following lines in the grub menu.lst, just before the BEGIN AUTOMAGIC KERNELS LIST

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro quiet splash
savedefault
boot


(note it doesnt have an initrd with it, so hopefully it already has most of what is essential before the filesystem is loaded)

try to boot with that kernel now... if this one works, we'll know its not a prob with conf files in the hdd, but if it doesn't, then I'm sorry, I can't think of anything else...:(

---

