---
title: "installed gfxboot: now can't boot windows"
date: 2006-12-21
forum: General Help
---

### Post by mrphd on 2006-12-21
Hi, I have installed gfxboot to give me a nice graphical boot screen for choosing between OS's after following the instructions on [http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855).

Well, I get a nice boot screen and I can still boot into ubuntu. However, I can no longer boot into windows. Neither can I see my windows partition from Edgy. It is important that I can still boot windows and that I can access my files.

Windows appears in gfxboot but after I select it it says "Grub loading stage 2", some text flashes far too quickly for me to see, and then it returns to the boot menu.

Please help me, someone...

P.S. fdisk -l gives me...

>  
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8686    69770263+   7  HPFS/NTFS
/dev/hda2            8687        9682     8000370   83  Linux
/dev/hda3            9683        9729      377527+   f  W95 Ext'd (LBA)
/dev/hda5            9683        9729      377496   82  Linux swap / Solaris


And my menu.lst file is:

> gfxmenu /boot/grub/message.suse
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
# kopt=root=UUID=92e7be31-01bb-4f8e-bd0c-18241c3ebe57 ro
# kopt_2_6=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by mrphd on 2006-12-22
Okay, I now have windows running again. I managed to find my recovery CD and used the recovery console. Running fixboot did the trick. Now I just need to get grub running again so I can dual boot...

---

### Post by mrphd on 2006-12-22
I have sorted out everything now. I used the latest Super Grub CD and selected Linux->Fix Boot of Linux (GRUB). Having done this, I can now boot into both Windows and Ubuntu again.

---

### Post by Sha-baz on 2006-12-28
Ok... you did *what*?
 
I seem to be having the same problem over here, I didn't even realize I couldn't reach my windows partition from Ubuntu but after I read your post I found out that I couldn't.
I did lots of things to GRUB and my splash screens before I got the boot problem, so this is unmistakably the same problem.
 
I understand that you used 2 boot CD's to fix this problem, could you please describe what the exact boot CD's were (maybe you have some hints for ISO's to download), and the steps you took to resolve this issue. It would be appreciated greatly...

---

### Post by mrphd on 2006-12-29
> **Sha-baz said:**
> Ok... you did *what*?

The first thing that I wanted to correct is the ability to boot into windows again. I was able to do this using the Windows XP CD that came with my computer. When you boot your computer with this CD in the drive it should give you the option to recover a windows installation (I can't remember exactly what this is called but it should be obvious). Anyway, it will start a console and just type fixboot. Now restart your computer.

Now you should just be able to boot into windows, and you will not be able to see grub. But the first thing to verify is that you can actually boot into windows.

Assuming this is the case we want to be able to restore GRUB so you can choose your OS. For this I used the super grub cd. You can get it from here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/). Select Linux->Fix Boot of Linux (GRUB) and reboot.

Hope this fixes things for you!

---

### Post by Sha-baz on 2006-12-29
> **mrphd said:**
> Hope this fixes things for you!

I think it will, thank you very much.
I'll let you know in (I hope) 15 minutes.

---

### Post by Sha-baz on 2006-12-29
Uh oh....
 
I can't seem to use my CD/DVD burner...(HDB does not exist) so here I am with an ISO I can't use...
Guess this solution will have to wait for another one first...

---

### Post by adrian15 on 2006-12-29
> **Sha-baz said:**
> Uh oh....
 
I can't seem to use my CD/DVD burner...(HDB does not exist) so here I am with an ISO I can't use...
Guess this solution will have to wait for another one first...

1st alternative: Boot with windows boot cd and type fixboot. Burn the ISO from Windows (windows will understand your cdrom burner drive)

2nd alternative: Download Super Grub Disk as a diskette and use

dd if=/path/to/fileimg of=/dev/fd0

to burn it into a floppy.

3rd alternative: USB super grub disk.  (I do not recommend it)

4th alternative: Use a friend's cdrom burner. :)

adrian15

---

### Post by Sha-baz on 2006-12-30
Thanks Adrian, but my problem has evolved into an entire range of problems. Floppy is not an option since I'm using Ubuntu on a Vaio laptop with no floppy drive. Furthermore I hate floppy's, all floppy's must die. I do however have a USB-stick but since you don't recommend using that as a boot device, I'll move that option down on my options list (yes, I actually have one)
 
I did try to use the Vista CD to repair the Windows startup sequence, but somehow that didn't work. Fixboot from an XP disc also didn't do the trick. But this is a Linux forum, and I consider this to be more of a Windows problem. Reinstalling Windows entirely is actually an option, since I got my data and mailsettings working from a third VFAT partition just in time, before this problem occured.
 
Thanks again!

---

