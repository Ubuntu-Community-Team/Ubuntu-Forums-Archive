---
title: "Problems with 6.06 Ubuntu and Windows Vista"
date: 2007-10-31
forum: General Help
---

### Post by TuxTwig on 2007-10-31
I've recently installed Ubuntu onto a partition of my hard drive. (I only have one) I've tried many different methods but I can't seem to access Vista now. I've tried editing my menu.lst file and my grub config but none of this seems to work. I've also tried a program called SuperGrubDisk but that was also useless. If anyone would take the time to help me, I would be very happy.:) 

I'm not sure if this is in the right sub-forum, sorry if it isnt.:(

I'm currently using GRUB as my bootloader. I need to access my Vista now to retrieve important files so I'd appreciate if people posted.

---

### Post by alwaysbutter on 2007-10-31
I'll give it a shot.  First of all, did ubuntu mount your vista partition?  If so browse the drive and back up your important data Then post makyour menu.lst file.  Are you getting grub errors or other errors?

---

### Post by TuxTwig on 2007-10-31
I think Ubuntu might have been installed onto my Vista partition but not entirely sure. Not sure how to backup since I can't access Vista but I have older versions of backups I've made previously. Here is my entire menu.lst file. I'm going to bed now so you won;t here from me till tommorow.:)

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
timeout		7

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single root (hd0,1)
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

I actually got rid of the Vista entry right before I posted this. No GRUB errors when running Linux. When trying to run Vista, all I get is the bar with the loading scroller thing and then my screen goes black. No windows logon or anything like that.

Thanks for your help.:)

---

### Post by alwaysbutter on 2007-10-31
Run gksu gparted and see if you overwrote the vista partition when you installed ubuntu.  We'll go from there.

---

### Post by TuxTwig on 2007-10-31
Is this run from Ubuntu? Where do I find it?

---

### Post by TuxTwig on 2007-10-31
Oh never mind I know where. I'll run it when I get back from school:) For some odd reason I can't access my C Drive (Vista Partition) or my D drive (spare) from Ubuntu..

---

### Post by TuxTwig on 2007-10-31
I ran the Gparted scan and I'm posting a screenie. Now i'm sure that Ubuntu hasnt mounted my Vista (C). The partition on the left is the Vista partition (/dev/sda/1) The size is still 60 something GBs as it had been before I installed Linux. Not quite sure what happened to the other partition (D), as I had some files on that Hard drive as well. As long as my C drive survives, everything is ok. :)

---

### Post by louieb on 2007-10-31
Fairly common question from the look of you GParted screen shot this will add VISTA to your  GRUB menu. Writen for XP but VISTA shound work the same
 **[You Install Ubuntu but Windows is not a boot option.]("http://louboldt.com/ilinuxgrub.htm#win1")**

---

### Post by TuxTwig on 2007-10-31
Thanks for responding louieb, I'll try this as soon as I get home. :)

---

### Post by TuxTwig on 2007-11-01
I tried editing the menu.lst file again (following the instructions on that page very carefully), but when I boot Vista, the same problem happens again. The code is right, but for some reason, the Windows Loading Screen comes up (the one with the scroller thing and Microsoft Corporation written below it) but after that my screen just goes dark. No Windows logon. I suspect maybe Linux changed my Graphics card setting or something to do with video because I'm obviously having no problem booting. Where can I find the Video settings in Ubuntu?

---

### Post by alwaysbutter on 2007-11-01
Can you boot into vista in safe mode?  I assume this exists in Vista, although I'm really not sure.

---

### Post by alwaysbutter on 2007-11-01
if possible to do safe mode try vga boot, then check your video card in the device manager.

---

### Post by TuxTwig on 2007-11-01
Same thing happens when I try to run Vista in Safe Mode.

---

### Post by TuxTwig on 2007-11-01
Loading screen>Blackness.

---

### Post by louieb on 2007-11-01
Do a shutdown. Turn the computer completely off. Go get a cup of coffee or a coke. You want to keep it off long enough to clear the video memory. A couple of minutes should do it. The video memory should have cleared just by rebooting. But sometime you have to do a complete shutdown to clear everything.

---

### Post by TuxTwig on 2007-11-01
Thank you louieb for the suggestion.

---

### Post by TuxTwig on 2007-11-01
I don't think the shutdown and wait method worked. Same thing happened again when I booted Vista. Any other good methods or ideas? Every suggestion counts. :)

---

### Post by Shazaam on 2007-11-01
Boot Ubuntu and run these commands in a terminal and post the output here...
```
sudo fdisk -lu
```
(small L)

```
cat /etc/fstab
```

---

### Post by TuxTwig on 2007-11-01
Thanks for posting Shazaam, I'm booting into Linux right now.

---

### Post by TuxTwig on 2007-11-01
The results of fdisk scan. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195302204    97651071    7  HPFS/NTFS
/dev/sda2       195302205   395472104   100084950    f  W95 Ext'd (LBA)
/dev/sda3       395472105   488392064    46459980   83  Linux
/dev/sda5       195302268   391471919    98084826    7  HPFS/NTFS
/dev/sda6       391471983   395472104     2000061   82  Linux swap / Solaris

The results of /cat/etc/fstab

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195302204    97651071    7  HPFS/NTFS
/dev/sda2       195302205   395472104   100084950    f  W95 Ext'd (LBA)
/dev/sda3       395472105   488392064    46459980   83  Linux
/dev/sda5       195302268   391471919    98084826    7  HPFS/NTFS
/dev/sda6       391471983   395472104     2000061   82  Linux swap / Solaris

---

### Post by TuxTwig on 2007-11-01
Waiting patiently for new replies... EDIT: Going to bed, any posts appreciated :)

---

### Post by TuxTwig on 2007-11-02
Back and ready for suggestions. K guys, I've made a new thread dedicated to my GRUB booting problem. Visit the thread here: [http://ubuntuforums.org/showthread.php?t=600997](http://ubuntuforums.org/showthread.php?t=600997) Be sure to post!

---

