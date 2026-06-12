---
title: "Grub error"
date: 2007-05-28
forum: General Help
---

### Post by emid on 2007-05-28
I just reinstalled Feisty after having some nvidia driver related issues that were taking too long for me to resolve.  I erased my previous Ubuntu partition and reinstalled on the resulting free space.  I have been dual booting and have an XP partition on the same drive as Ubuntu. The install seemed to finish successfully.  Upon restarting I am brought to the Grub menu which shows me my new Ubuntu install and my windows install.  However, if I select Ubuntu it gives me the following:

"Error 22: No Such Partition"

If I select Windows XP it gives me:

"Error 13: Invalid or unsupported executable format"

I rebooted with the Feisty install cd and selected to boot from the hard disk.  When I did this it proceeded to show me the same grub menu.  except this time it would boot into whatever I selected.  Can anyone tell me what I have to do to fix this problem?  Is it something related to the MBR?  Any help would be awesome.  I really don't want to have to keep booting from the cd in addition to the fact that I cannot get into my XP install.

---

### Post by confused57 on 2007-05-28
If you would, boot the live cd, open a terminal and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

From the output of the above, mount your root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu
```
substitute your root partition for sda2...

then post the output of:
```
gedit /media/ubuntu/boot/grub/menu.lst
```

IF you have more than one hard drive:
```
gedit /media/ubuntu/boot/grub/device.map
```

---

### Post by emid on 2007-05-28
When you say to boot the live cd, do you mean to boot into my new ubuntu install using the live cd or actually boot the live cd.  I think you mean boot the actual live cd, but I just want to make sure.

---

### Post by confused57 on 2007-05-28
> **emid said:**
> When you say to boot the live cd, do you mean to boot into my new ubuntu install using the live cd or actually boot the live cd.  I think you mean boot the actual live cd, but I just want to make sure.

I did mean the live cd, but I forgot you were able to access your Ubuntu install using the live cd...use your Ubuntu install, you won't have to mount it as you would with the live cd.  
In your Ubuntu install post "sudo fdisk -l" as before, and:
```
gedit /boot/grub/menu.lst
```

and possibly
```
gedit /boot/grub/device.map
```
if you have 2 hard drives.

---

### Post by emid on 2007-05-28
Here are the results of my fdisk -l, I actually have more than two hard drives,

sda is the drive where both my Ubuntu and XP installs are as you can see.

```


Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14352   115282408+   7  HPFS/NTFS
/dev/sda2           14353       19237    39238762+  83  Linux
/dev/sda3           19238       19452     1726987+   5  Extended
/dev/sda5           19238       19452     1726956   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       30400   244179967+   f  W95 Ext'd (LBA)
/dev/hda5               2       30400   244179936    7  HPFS/NTFS

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4982    40017883+  83  Linux

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4864    39070048+   b  W95 FAT32



```

---

### Post by emid on 2007-05-28
Here is the contents of my menu.lst file.  Bear with me as it is quite long.

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
# kopt=root=UUID=55b3ab9c-4f88-4b6a-b60e-a033099b3c8a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=55b3ab9c-4f88-4b6a-b60e-a033099b3c8a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=55b3ab9c-4f88-4b6a-b60e-a033099b3c8a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=55b3ab9c-4f88-4b6a-b60e-a033099b3c8a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=55b3ab9c-4f88-4b6a-b60e-a033099b3c8a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1



```

Here is my device,map file:

```


(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda
(hd3)	/dev/sdb
(hd4)	/dev/sdc

```

Thanks for the help.

---

### Post by confused57 on 2007-05-28
You might also need to post the output of:
```
gedit /boot/grub/device.map
```
this will give an idea of how grub recognizes the order of your hard drives...
nevermind, just saw you posted it.

Added:  It looks like grub is installed to /dev/hda...are you sure that your bios is booting first to this drive?  I'm wondering if it's possible that you're trying to boot your old grub menu, which might be installed on another drive's mbr.

---

### Post by emid on 2007-05-28
I see, does this mean that I need to reorder my device.map file so that sda is at the top?

---

### Post by confused57 on 2007-05-28
> **emid said:**
> I see, does this mean that I need to reorder my device.map file so that sda is at the top?

No, don't do that...if you're booting first to your hda drive in bios, the entries you have "should" boot Ubuntu & Windows.  What you might try is reinstall grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by emid on 2007-05-28
That's a good question.  To be honest I'm not really sure.  I just know that when I boot my computer normally, the entries available in Grub reflect the new installation and my XP installation.  So it seems as though it sees which OS'es I have currently installed.

---

### Post by confused57 on 2007-05-28
> **emid said:**
> That's a good question.  To be honest I'm not really sure.  I just know that when I boot my computer normally, the entries available in Grub reflect the new installation and my XP installation.  So it seems as though it sees which OS'es I have currently installed.

If reinstalling grub doesn't work...you could do some "trial & error" to possibly find the correct root entry.  What you would try is at the grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd2,1) to
(hd1,1), then press "b" to boot.  Keep trying different hard drives entries, i.e. (hd0,1), (hd3,1), & (hd4.1).

You could also try grub's Command Line Interface(CLI), by press "c" at the grub boot menu, to find an entry to boot your OS:
[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

Added:  Another suggestion would be to boot into Ubuntu, download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's a small download(5-7 Mb), but it should be able to boot your Ubuntu or Windows OSes.  Use the 2nd download mirror in the link above.

---

### Post by emid on 2007-05-28
Reinstalling Grub didn't seem to fix it.  I still have the same problem as before.  I'm going to try what you suggested with regards to trial and error and see what happens.  I'll post my results.  Once again, I really appreciate your help.

---

### Post by confused57 on 2007-05-28
> **emid said:**
> Reinstalling Grub didn't seem to fix it.  I still have the same problem as before.  I'm going to try what you suggested with regards to trial and error and see what happens.  I'll post my results.  Once again, I really appreciate your help.

It's after 3 AM here, so I'm not going to be able to help much more tonight...I would highly recommend that you burn a copy of the Super Grub Disk, I believe it would be your best bet if you're not able to get your system booting any other way.

---

### Post by emid on 2007-05-28
I set it to (hd0,1) and it worked.  Now I have to see what's up with the XP install.  At least we're getting somewhere.

Yeah I think we're in the same time zone, I should be going to bed as well.  Thanks for all your help, at least now I can boot into Ubuntu.

---

### Post by confused57 on 2007-05-28
> **emid said:**
> I set it to (hd0,1) and it worked.  Now I have to see what's up with the XP install.  At least we're getting somewhere.

Yeah I think we're in the same time zone, I should be going to bed as well.  Thanks for all your help, at least now I can boot into Ubuntu.

OK, we're getting somewhere...your Window's root would be (hd0,0) and you won't need the mapping lines in your Window's grub entry.   These changes are temporary, but they can be made permanent in your /boot/grub/menu.lst.

Added:  I'm guessing that you're booting first to your sda drive, and somehow grub incorrectly identified the order of your hard drives, by your device.map.
If for some reason, Windows won't boot, it's possible that your device.map may need to read (hd0) /dev/sda?  Good luck with it...there's plenty of other experience people on the forum that may be able to provide an explanation of what might be going on...I'll check back in later on today to see how it's going.

---

### Post by dusie on 2007-05-28
After upgrading to kernel  2.6.20-16 I, too, received the same error 22 from grub for _both_ the -15 and -16 kernels and was, therefore, unable to get into Ubuntu.  The solution for me was to press "e" when in the grub menu and edit the **root** line.  The upgrade had changed the line from root (hd0,7) to root (hd0,2).  When corrected everything now works.  ;)

  The problems with the kernel upgrade seem to vary from system to system, but the error 22 seems to be easily fixed with the help of the Ubuntu community.

---

### Post by confused57 on 2007-05-28
> **dusie said:**
> After upgrading to kernel  2.6.20-16 I, too, received the same error 22 from grub for _both_ the -15 and -16 kernels and was, therefore, unable to get into Ubuntu.  The solution for me was to press "e" when in the grub menu and edit the **root** line.  The upgrade had changed the line from root (hd0,7) to root (hd0,2).  When corrected everything now works.  ;)

  The problems with the kernel upgrade seem to vary from system to system, but the error 22 seems to be easily fixed with the help of the Ubuntu community.

You might need to edit your groot line:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

