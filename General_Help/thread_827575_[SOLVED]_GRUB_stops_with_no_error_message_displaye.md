---
title: "[SOLVED] GRUB stops with no error message displayed."
date: 2008-06-12
forum: General Help
---

### Post by snl2587 on 2008-06-12
I have no idea why, but after running a fresh Hardy install with no issues for about three weeks, I suddenly can't boot. This is all I see:
```
GRUB _
```
Here's what I did between my last successful boot and this freeze:
[LIST=1]
[*]I installed the latest batch of updates
[*]I installed Acetone2ISO (and ran it)
[/LIST]
And that's it.

Fortunately for me, I dual-boot with XP and never placed GRUB in the MBR (instead running it from (hda0,1)), so I'm still able to do most things.

If anyone can help me I'd really appreciate it. Otherwise I'll just wipe and reinstall.

(I'm running on an HP dv5210us, if that helps).

---

### Post by VMC on 2008-06-12
> **snl2587 said:**
> I have no idea why, but after running a fresh Hardy install with no issues for about three weeks, I suddenly can't boot. This is all I see:
```
GRUB _
```
Here's what I did between my last successful boot and this freeze:
[LIST=1]
[*]I installed the latest batch of updates
[*]I installed Acetone2ISO (and ran it)
[/LIST]
And that's it.

Fortunately for me, I dual-boot with XP and never placed GRUB in the MBR (instead running it from (hda0,1)), so I'm still able to do most things.

If anyone can help me I'd really appreciate it. Otherwise I'll just wipe and reinstall.

(I'm running on an HP dv5210us, if that helps).
Two things.
1. I downloaded that "Acetone2ISO", and threw it away. Not sure if it caused any problems, but I found out that FileRoller was able to open up ISO and did a much better job of doing so.
2. How did you boot without using MBR?
   Do this from a Terminal:
```
cat /etc/fstab
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by snl2587 on 2008-06-12
The Windows bootloader is in the MBR, and through a modification to the Windows boot.ini I use that to reach GRUB, which I then use to boot Ubuntu. And for nearly 8 months of using various versions of Ubuntu that's worked flawlessly.

Unfortunatly, I do not have a shell to run fdisk as I cannot start the kernel. Through an external reader, here is menu.lst:

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
# kopt=root=UUID=9faee541-062f-42ab-9e70-ce8fa314b2a7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9faee541-062f-42ab-9e70-ce8fa314b2a7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9faee541-062f-42ab-9e70-ce8fa314b2a7 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

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
chainloader	+1

```
(I changed the crashdump thing, but AFTER it had already crashed as described)

and, /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=9faee541-062f-42ab-9e70-ce8fa314b2a7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=46BB-88E8  /osshare        vfat    utf8,user,umask=000,gid=46 0       1
# /dev/hda5
UUID=137948e3-a040-41df-817a-e1b8fc3a77f1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Thanks in advance.

---

### Post by meierfra. on 2008-06-13
Since  you installed grub to a partition, the stage1.5 files are not used and you do not get any error messages. 

I suggest to get SuperGrub (see my signature) Supergrub can install Grub to the MBR and restore the MBR within minutes. It might also be able to boot you into ubuntu or at least produce some  better error messages. 

> I do not have a shell to run fdisk as I cannot start the kernel.

Do you have a Ubuntu Live CD, or any kind of LiveCD (gparted, PartedMagic, SystemRescue,.....) If not, you should really get one.

---

### Post by snl2587 on 2008-06-13
> I suggest to get SuperGrub (see my signature) Supergrub can install Grub to the MBR and restore the MBR within minutes. It might also be able to boot you into ubuntu or at least produce some better error messages.
I'm not too keen on installing GRUB to the MBR, especially after this. Is there a way to fix GRUB on the second partition only?

And I do have a live CD (latest SystemRescue), but I wasn't sure if it would correctly give me the same output. Plus I already know the partition structure and know that the Windows MBR is correctly grabbing the second partition to try and load grub...

---

### Post by VMC on 2008-06-13
From Terminal type grub, then follow the below text. Read the red text for your situation:

Once started, GRUB will show the command-line interface (*note
Command-line interface::). First, set the GRUB's "root device"(1)
(*note Installing GRUB natively-Footnote-1::) to the boot directory,
like this:

grub> root (hd0,0)

If you are not sure which partition actually holds these files, use
the command `find' (*note find::), like this:

grub> find /boot/grub/stage1

This will search for the file name `/boot/grub/stage1' and show the
devices which contain the file.

Once you've set the root device correctly, run the command `setup'
(*note setup::):

grub> setup (hd0)

This command will install GRUB on the MBR in the first drive. [COLOR="Red"]If you
want to install GRUB into the "boot sector" of a partition instead of
the MBR, specify a partition into which you want to install GRUB:

grub> setup (hd0,0)[/COLOR]

If you install GRUB into a partition or a drive other than the first
one, you must chain-load GRUB from another boot loader. Refer to the
manual for the boot loader to know how to chain-load GRUB.

---

### Post by meierfra. on 2008-06-13
You can try supergrub   even without installing grub to the MBR.  Just try   booting Ubuntu with it. We  need to see some error messages.

But  restoring the MBR with Supergrub  is very easy. Just choose "Win->MBR Win" at the first screen. There really is nothing to worry about.   

> And I do have a live CD (latest SystemRescue), but I wasn't sure if it would correctly give me the same output.

System Rescue will give the correct output.


> Plus I already know the partition structure

But I would like to see the sizes and exact location of your partitions


> 
Is there a way to fix GRUB on the second partition only?

You can reinstall grub to the second partition with

```
grub
root (hd0,1)
setup (hd0,1)
quit
```

from a terminal in the  System Rescue CD. You can also you  use Supergrub do to that for you. 

After  that you  have to use "dd" to copy the boot sector  of the Ubuntu partition to a file on you C: drive, just like you did  when you added "ubuntu" to the Windows boot loader in the first place.
(Let me know if you need more details)

But I'm not sure that this will fix your problem.

---

### Post by snl2587 on 2008-06-13
I initially posted that following the instructions failed, except that I skipped making the .bin file for Windows. After I did, everything worked fine. Thanks for the help!

One quick thing, though: the instructions for GRUB do not work when using the Ubuntu LiveCD, only with another LiveCD. I have no idea why.

Also, here is my fdisk -l printout:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6077    48813471    7  HPFS/NTFS
/dev/sda2            6078        7161     8707230   83  Linux
/dev/sda4            7162        7296     1084387+   5  Extended
/dev/sda5            7163        7200      305235   82  Linux swap / Solaris
/dev/sda6            7201        7296      771088+   b  W95 FAT32

```
 (The partitions appear as hda's on the Ubuntu LiveCD...the above was from SystemRescueCD)

---

### Post by meierfra. on 2008-06-13
> One quick thing, though: the instructions for GRUB do not work when using the Ubuntu LiveCD, only with another LiveCD. I

Sorry, I didn't realize you had the Ubuntu LiveCD.  On the Ubuntu CD,  "grub" needs to be replaced by "sudo grub". On "SystemRescue" one is automatically  logged in as root.

> After I did, everything worked fine. 

So your problem is solved?

---

### Post by snl2587 on 2008-06-13
> So your problem is solved? Yes. Thanks for your help!

---

