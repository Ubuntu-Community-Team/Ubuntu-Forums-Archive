---
title: "Error With FSCK on Boot"
date: 2007-11-08
forum: General Help
---

### Post by kshane on 2007-11-08
When I boot up, it stops at a maintenance shell and references this log (below).  I've looked all around and can't figure it out.  After I exit the maint shell, it boots okay and everything seems to work, but I would like to get a clean boot.  Can any one help with this?

```
Log of fsck -C -R -A -a 
Wed Nov  7 20:44:56 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda4: clean, 2687/6979584 files, 7990469/13952452 blocks
/dev/sda2 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Wed Nov  7 20:44:56 2007
----------------
```

Here's my FSTAB:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7198D00F73629629 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=5e70c11b-d4a5-4cd6-9c1a-4a81e11ecffe /media/sda4     ext3    defaults        0       2
# /dev/sda5
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=ebf9e319-ccac-4b71-b585-88c0cea88134 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Thanks!

Kevin

---

### Post by Tyche on 2007-11-08
Have you by any chance re-partitioned recently?  And if so, are you booting off of a second partition rather than your first?  This looks very much like the problem I had after doing just that very thing.  If so, then your UUID numbers may not be correct.  In a terminal, use the command:

blkid

This will tell you the UUID numbers of all your partitions, along with the /dev location.
I hope this helps

---

### Post by kshane on 2007-11-08
> **Tyche said:**
> Have you by any chance re-partitioned recently?  And if so, are you booting off of a second partition rather than your first?  This looks very much like the problem I had after doing just that very thing.  If so, then your UUID numbers may not be correct.  In a terminal, use the command:

blkid

This will tell you the UUID numbers of all your partitions, along with the /dev location.
I hope this helps


I did do some partition changes today, but the UUIDs match, as far as I can tell.   sda1 is Vista.  sda2 is Ubuntu and sda5 is eLive (there is no sda3)  sda4 is a storage partition for Linux and sda6 is swap.  Is maybe the lack of an sda3 the problem? 

```

kevin@enigma:~$ blkid
/dev/sda1: UUID="7198D00F73629629" TYPE="ntfs" 
/dev/sda2: UUID="c1dd7906-ecf3-403c-8348-9701b828e691" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="5e70c11b-d4a5-4cd6-9c1a-4a81e11ecffe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="83439956-e2da-44a3-b253-019e2fc06f6a" TYPE="reiserfs" 
/dev/sda6: TYPE="swap" UUID="fd84d834-fa0b-47f2-9900-486af5e01561" 

```

Kevin

---

### Post by niteshifter on 2007-11-08
fsck is telling you "operational error" (exit status or 8), because it is wants to check the filesystem on /dev/sda2 - which is the root of your filesystem. It's mounted (it has your /boot folder) and fsck can not operate upon a mounted filesystem.

(BTW: this is why separate /boot and /root partitions are sooo very handy!).

It wants to because A) it's time to do this, B) More than XX mounts have been done (XX is typically 30) or C) there's a problem in the filesystem.

Boot from a LiveCD and run fsck -N /dev/sda2 and if that output is not too scary-looking run fsck /dev/sda2.

---

### Post by kshane on 2007-11-08
> **niteshifter said:**
> fsck is telling you "operational error" (exit status or 8), because it is wants to check the filesystem on /dev/sda2 - which is the root of your filesystem. It's mounted (it has your /boot folder) and fsck can not operate upon a mounted filesystem.

(BTW: this is why separate /boot and /root partitions are sooo very handy!).

It wants to because A) it's time to do this, B) More than XX mounts have been done (XX is typically 30) or C) there's a problem in the filesystem.

Boot from a LiveCD and run fsck -N /dev/sda2 and if that output is not too scary-looking run fsck /dev/sda2.

Thanks, but I guess I'm not up to this.  I'm gonna have to do some reading on this.  Thanks very much for you help, though!

Kevin

---

### Post by kshane on 2007-11-08
I have re3cently made some changes to my partitions on my main (only) hdd.  The changes have bee reversed, but now I get errors each time I boot and it goes to a shell instead of the login screen.  I ran FSCK through the Trinity Rescue Kit and there e are no errors.  I am given to understand that the reason for the errors is that the system is trying to run fsck on a mounted partition (sda,2).  I am totally lost as to what t odo about this.  I would love to be able to just boot to teh login screen.  Below are the error screen, fstab, menu.lst and a listing of the UUIDs for my partitions.  If some one could help me get this straightened out, I would be terribly grateful!

UUIDs:
```

kevin@enigma:~$ blkid
/dev/sda1: UUID="7198D00F73629629" TYPE="ntfs" 
/dev/sda2: UUID="c1dd7906-ecf3-403c-8348-9701b828e691" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="5e70c11b-d4a5-4cd6-9c1a-4a81e11ecffe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="83439956-e2da-44a3-b253-019e2fc06f6a" TYPE="reiserfs" 
/dev/sda6: TYPE="swap" UUID="fd84d834-fa0b-47f2-9900-486af5e01561" 

```

ERROR NOTICE:
```

Log of fsck -C -R -A -a 
Thu Nov  8 10:16:05 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda4: clean, 2687/6979584 files, 7990469/13952452 blocks
/dev/sda2 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Thu Nov  8 10:16:05 2007

```

FSTAB:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7198D00F73629629 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=5e70c11b-d4a5-4cd6-9c1a-4a81e11ecffe /media/sda4     ext3    defaults        0       2
# /dev/sda5
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=ebf9e319-ccac-4b71-b585-88c0cea88134 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

MENU.LST:
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
timeout		30

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
# kopt=root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title Elive Gem  
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /boot/vmlinuz-2.6.18-elive root=/dev/hda5 vga=791 splash=silent
initrd /boot/initrd.img-2.6.18-elive

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

I would so appreciate any help!  Thanks in advance...

Kevin

---

### Post by dabl on 2007-11-08
It almost looks like fsck is trying to run AFTER /dev/sda2 is mounted -- that won't work.

Unfortunately, /dev/sda2 is your root filesystem, so that means (a) it's very important that you get this problem fixed, and (b) you can't unmount it while running, like you could other partitions.

So, I'd say boot a Live CD, and then run fsck on /dev/sda2 that way.  Let it correct any errors that it finds. :)

---

### Post by kshane on 2007-11-08
> **dabl said:**
> It almost looks like fsck is trying to run AFTER /dev/sda2 is mounted -- that won't work.

Unfortunately, /dev/sda2 is your root filesystem, so that means (a) it's very important that you get this problem fixed, and (b) you can't unmount it while running, like you could other partitions.

So, I'd say boot a Live CD, and then run fsck on /dev/sda2 that way.  Let it correct any errors that it finds. :)

I did boot to the Trinity disk and ran fsck.  It comes up okay.  But I get this error every time I boot.  How can I resolve this?  Apparently it IS mounting sda2 then running fsck.  While I DO have some changes, the basic structure is the same as it has been for months, but suddenly this error...

---

### Post by mcduck on 2007-11-08
The UUID for sda5 is wrong in your fstab. You actually have there the same UUID as your root partition has. Also if the partition is using ReiserFS, you can't mount it as Ext3 (like your fstab is saying).

```

/dev/sda2: UUID="c1dd7906-ecf3-403c-8348-9701b828e691" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="83439956-e2da-44a3-b253-019e2fc06f6a" TYPE="reiserfs"
```
```

# /dev/sda5
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /media/sda5     ext3    defaults        0       2
```

Apart from those, using fsck for windows partitions seems to cause problems on some machines. And even if it works, it should be done after checking root partition, not at the same time. Change the last number on this line from 1 to either 0 (to disable fsck) or 2 (to check the partition after root):
```
# /dev/sda1
UUID=7198D00F73629629 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
```

edit. Your fstab also has wrong UUID for swap:
```
/dev/sda6: TYPE="swap" UUID="fd84d834-fa0b-47f2-9900-486af5e01561"
```
```
# /dev/sda6
UUID=ebf9e319-ccac-4b71-b585-88c0cea88134 none            swap    sw              0       0
```

---

### Post by kshane on 2007-11-08
> **mcduck said:**
> The UUID for sda5 is wrong in your fstab. You actually have there the same UUID as your root partition has. Also if the partition is using ReiserFS, you can't mount it as Ext3 (like your fstab is saying).

```

/dev/sda2: UUID="c1dd7906-ecf3-403c-8348-9701b828e691" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="83439956-e2da-44a3-b253-019e2fc06f6a" TYPE="reiserfs"
```
```

# /dev/sda5
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /media/sda5     ext3    defaults        0       2
```

Apart from those, using fsck for windows partitions seems to cause problems on some machines. And even if it works, it should be done after checking root partition, not at the same time. Change the last number on this line from 1 to either 0 (to disable fsck) or 2 (to check the partition after root):
```
# /dev/sda1
UUID=7198D00F73629629 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
```

edit. Your fstab also has wrong UUID for swap:
```
/dev/sda6: TYPE="swap" UUID="fd84d834-fa0b-47f2-9900-486af5e01561"
```
```
# /dev/sda6
UUID=ebf9e319-ccac-4b71-b585-88c0cea88134 none            swap    sw              0       0
```

Thank you, thank you, thank you!  I made the changes suggested and it works fine, now.  I injured my neck and have been home for several days and taking pain pills/muscle relaxers.  They are not conducive to very cerebral undertakings, so I have been missing some very easy things, such as simply comparing UUIDs to make sure there arte no errors.  Your patience with my foolish questions is very appreciated...

Thanks again...

Kevin

---

