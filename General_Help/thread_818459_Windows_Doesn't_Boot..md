---
title: "Windows Doesn't Boot."
date: 2008-06-04
forum: General Help
---

### Post by ForksHolder on 2008-06-04
Hello,

Since the update to Hardy, my Windows XP partition doesn't load.

My fdisk -l output is:

> holder@holder-laptop:~$ sudo fdisk -l
[sudo] password for holder: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3bac3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4227    33951928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4228        9729    44194815    f  W95 Ext'd (LBA)
/dev/sda5            4228        4419     1542208+  82  Linux swap / Solaris
/dev/sda6            4420        9729    42652543+  83  Linux


I have no idea why this happend..

Any ideas?

EDIT:
Here's my menu.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro

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

title		Debian GNU/Linux, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro single
initrd		/boot/initrd.img-2.6.24-18-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro single
initrd		/boot/initrd.img-2.6.24-17-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional (TuneUp Backup)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by Xiong Chiamiov on 2008-06-05
Hmm, /dev/sda1 matches (hd0,0), so there shouldn't be any problem there.

When you say "doesn't boot", what kind of error are you getting?

It most likely was a problem with your grub menu being updated automagically, but incorrectly.  You can prevent that from happening in the future by changing this
```

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

```
to this
```

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=true

```

---

### Post by ForksHolder on 2008-06-05
The error is that when i choose the Windows XP partition, it makes a real quick error witch i can't even see what is write in, then gets back to the boot manu.. =/

I didn't really understand what to change and where.. can you explain?

---

### Post by ForksHolder on 2008-06-06
Bump?

---

### Post by briandu on 2008-06-06
when in ubuntu open xterm

enter:
sudo grub-install /dev/sda

and it will recreate the grub menu.lst correctly

easiest method I think

---

### Post by lmc on 2008-06-06
Has anyone tried this? ^^^

I also have this problem now. I *stupidly* commented out older versions of ubuntu earlier because the list was getting so long when booting up that I had to scroll down for a bit to get to my windows XP partition.
anyways it all went a bit wrong, and no, I never backed up my /grub/boot/menu.lst (own fault for being THICK).

then what happened when I rebooted was that it took a LONG LONG time to even boot up and by the time it did, I wasn't able to select any of the options to boot into windows.
It booted into kubuntu, but it did take a very, very long time.

I have to stop doing these stupid things when I have deadlines.

my question: I'm scared to write
sudo grub-install /dev/sda

are there any adverse effects if I do and it doesn't work??

---

### Post by lmc on 2008-06-06
actually that doesn't work for me!

---

### Post by ForksHolder on 2008-06-09
> **lmc said:**
> actually that doesn't work for me!

Agreed.

---

### Post by Habbit on 2008-06-09
If you cannot see the error, try to enter the commands listed under "Windows XP" yourself, so that GRUB is not in "script" mode and you can see the error (remember to issue the "boot" command last, which is usually not written in the script).

---

### Post by ForksHolder on 2008-06-10
> **Habbit said:**
> If you cannot see the error, try to enter the commands listed under "Windows XP" yourself, so that GRUB is not in "script" mode and you can see the error (remember to issue the "boot" command last, which is usually not written in the script).

It says something with "Unknown partition" or something like that

---

### Post by Habbit on 2008-06-10
Try changing the root line to "rootnoverify (hd0,0)" so that GRUB doesn't check anything about the partition other than its existence.

---

### Post by litemotiv on 2008-06-10
same here, hardy just killed my ntfs partition. :-(

```

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

i fear it might be caused by this... [Random file corruptions in ntfs-3g < 1.2506](https://bugs.launchpad.net/ubuntu/hardy/+source/ntfs-3g/+bug/229000)

---

### Post by ForksHolder on 2008-06-11
> **Habbit said:**
> Try changing the root line to "rootnoverify (hd0,0)" so that GRUB doesn't check anything about the partition other than its existence.

That's not working.. same error..

> **litemotiv said:**
> same here, hardy just killed my ntfs partition. :-(

```

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

i fear it might be caused by this... [Random file corruptions in ntfs-3g < 1.2506](https://bugs.launchpad.net/ubuntu/hardy/+source/ntfs-3g/+bug/229000)


Same error to me..

Any ideas? ><"

---

### Post by Tomatz on 2008-06-11
In a terminal:

```
sudo gedit /boot/grub/menu.lst
```

Then scroll to the bottom and overwrite the windows entry with this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional (TuneUp Backup)
root (hd0,0)
savedefault
makeactive
map		(hd0) (hd0)
map		(hd0) (hd0)
chainloader +1

```

Save


I had this problem all i needed was the "map" entrys ;)

---

### Post by litemotiv on 2008-06-11
> **ForksHolder said:**
> That's not working.. same error..

Same error to me..

Any ideas? ><"

i just got it working again. :)

it seems the partition table got corrupted somehow, i used the program Testdisk to fix it:

```

sudo aptitude install testdisk
sudo testdisk

```

the steps i took:

- analyse the drive (first option)
- find all partitions (it detected the ntfs-partition fine)
- rewrite the partition table to disk. 

after that i closed the program and rebooted, that's it. ;)

---

### Post by ForksHolder on 2008-06-11
> **Tomatz said:**
> In a terminal:

```
sudo gedit /boot/grub/menu.lst
```

Then scroll to the bottom and overwrite the windows entry with this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional (TuneUp Backup)
root (hd0,0)
savedefault
makeactive
map		(hd0) (hd0)
map		(hd0) (hd0)
chainloader +1

```

Save


I had this problem all i needed was the "map" entrys ;)

Now i see a different error:

"Unrecognized Partition."

Any ideas?

---

### Post by Tomatz on 2008-06-12
> **ForksHolder said:**
> Now i see a different error:

"Unrecognized Partition."

Any ideas?

Use your xp discs recovery console to run chkdsk.

Just put the disc in the drive, boot and wait for it to prompt you (bottom of the screen) to "press r for recovery console"

Once in the recovery console type

```
chkdsk /r

```
Hopefully its just filesystem errors and this will fix the problem.

;)

---

### Post by ForksHolder on 2008-06-12
Still nothing works of what you suggest.. the same error all along =/

---

### Post by Tomatz on 2008-06-12
> **ForksHolder said:**
> Still nothing works of what you suggest.. the same error all along =/

Download this and burn the iso to disc:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

Then boot with the supergrub disc in the drive and try to boot windows with it.

---

