---
title: "Problem configuring GRUB"
date: 2005-08-27
forum: General Help
---

### Post by arcanistherogue on 2005-08-27
Hey.  I recently installed Slackware linux on /dev/hdd.   I have no clue about GRUB, where it lists the hard drives as something else.  It is like (hd2,0), and I don't know how to configure GRUB so it also lists slackware.

I was told to edit /boot/grub/menu.lst, and I had a bit of trouble.  I could see how to edit it from the other examples, but I don't know what to put as hdd.  I have 5 drives in my computer:  

-CD Drive (It is listed as hda when i mount the drive)
-DVD Burner (listed as hdb)
-SATA Drive (listed as sda)
-ATA Hard drive (listed as hdc)
-ATA Hard drive (listed as hdd)

I have windows xp on hdc, and slackware on hdd.  I have Ubuntu on sda, and when I am configuring the menu.lst it says root for ubuntu is (hd2,0).  I don't know what to put as hdd, (hd1,0)?  I was thinking this, as c might be (hd0,0), but I really don't know.  

Also, to finish it off, all I need to do is fill it out like the others?  I know what to put for kernel, but i don't know what to do for "initrd".  What should I put here? 

And is there an easier way to get GRUB to detect this partition?

Thanks alot to anyone who at least took the time to read that :D

---

### Post by arnieboy on 2005-08-27
[QUOTE=arcanistherogue]Hey.  I recently installed Slackware linux on /dev/hdd.   I have no clue about GRUB, where it lists the hard drives as something else.  It is like (hd2,0), and I don't know how to configure GRUB so it also lists slackware.

I was told to edit /boot/grub/menu.lst, and I had a bit of trouble.  I could see how to edit it from the other examples, but I don't know what to put as hdd.  I have 5 drives in my computer:  

-CD Drive (It is listed as hda when i mount the drive)
-DVD Burner (listed as hdb)
-SATA Drive (listed as sda)
-ATA Hard drive (listed as hdc)
-ATA Hard drive (listed as hdd)

I have windows xp on hdc, and slackware on hdd.  I have Ubuntu on sda, and when I am configuring the menu.lst it says root for ubuntu is (hd2,0).  I don't know what to put as hdd, (hd1,0)?  I was thinking this, as c might be (hd0,0), but I really don't know.  

Also, to finish it off, all I need to do is fill it out like the others?  I know what to put for kernel, but i don't know what to do for "initrd".  What should I put here? 

And is there an easier way to get GRUB to detect this partition?

Thanks alot to anyone who at least took the time to read that :D[/QUOTE]

ok we will go step by step here. First of all please  post the contents of:
```
sudo fdisk -l /dev/hdd
```

---

### Post by arcanistherogue on 2005-08-28
> john@kubuntu:~$ sudo fdisk -l /dev/hdd
Password:

Disk /dev/hdd: 17.0 GB, 17020329984 bytes
16 heads, 63 sectors/track, 32979 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot.......Start........End......Blocks..........Id......System
/dev/hdd1.. *...........1.......29064....14648224+....83....Linux
/dev/hdd2............29065....30056.....499968 ........82....Linux swap / Solaris
john@kubuntu:~$


ehh... but I already knew that, I made those today (now yesterday) with fdisk

EDIT: added "."'s to make it easier to read.

---

### Post by arnieboy on 2005-08-28
[QUOTE=arcanistherogue]ehh... but I already knew that, I made those today (now yesterday) with fdisk

EDIT: added "."'s to make it easier to read.[/QUOTE]
ok assuming u know how to mount a filesystem please mount */dev/hdd1* and then *cd* to the */boot* folder of that partition and tell me the contents of *ls -l*

---

### Post by arcanistherogue on 2005-08-28
I do know how to mount, but would there be any special parameters?  I remember when I mounted my windows drive I had to do all this extra stuff, but will I need to do that?  

Actualy, I remember from my gentoo guide it had a bit on mounting ext3 filesystems.... hold on.

got it.

> root@kubuntu:/media/Slackware/boot # ls -l
total 1884
lrwxrwxrwx  1 root root      37 Aug 27 16:09 README.initrd -> /usr/doc/mkinitrd-1.0.1/README.initrd
lrwxrwxrwx  1 root root      21 Aug 27 16:09 System.map -> System.map-ide-2.4.29
-rw-r--r--  1 root root  607998 Jan 20  2005 System.map-ide-2.4.29
lrwxrwxrwx  1 root root      17 Aug 27 16:09 config -> config-ide-2.4.29
-rw-r--r--  1 root root   41731 Jan 20  2005 config-ide-2.4.29
-rw-r--r--  1 root root    5032 May 21  2004 diag1.img
lrwxrwxrwx  1 root root      18 Aug 27 16:09 vmlinuz -> vmlinuz-ide-2.4.29
-rw-r--r--  1 root root 1253760 Jan 20  2005 vmlinuz-ide-2.4.29


---

### Post by arnieboy on 2005-08-28
[QUOTE=arcanistherogue]I do know how to mount, but would there be any special parameters?  I remember when I mounted my windows drive I had to do all this extra stuff, but will I need to do that?  

Actualy, I remember from my gentoo guide it had a bit on mounting ext3 filesystems.... hold on.

got it.[/QUOTE]
great now we have all the info that we needed.  Now do this:
sudo gedit /boot/grub/menu.lst
when the file opens look for the place where u have something similar (NOT EXACTLY THE SAME) to this:
```
title		Ubuntu, kernel 2.6.10-5-686-smp 
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.10-5-686-smp root=/dev/hda7 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.10-5-686-smp
savedefault
boot
```
Just below this paragraph leave one line and add the following lines:
```
title            Slackware 10.1
root            (hd3,0)
kernel          /boot/vmlinuz-ide-2.4.29 ro root=/dev/hdd1
boot
```
save and exit. and reboot. let me know if u have any questions.

---

### Post by arcanistherogue on 2005-08-28
You sure its on hd2,0?  thats what ubuntu is listed as in the menu.lst file...

---

### Post by arnieboy on 2005-08-28
[QUOTE=arcanistherogue]You sure its on hd2,0?  thats what ubuntu is listed as in the menu.lst file...[/QUOTE]
how many hard drives do u have? if u have only two, then change it to (hd1,0). try rebooting. dont worry. nothing will crash. if u cant loginto slackware just paste the contents of 
sudo fdisk -l
whe u come back
the reason why I suggested hd2,0 is because u mentioned that its probably hd2,0 in your first post and I assumed u have 3 hard drives and u know what u are saying.

---

### Post by arcanistherogue on 2005-08-28
I tried both hd1,0 and hd2,0, both said file not found.  lemme paste the results of the command you said, hold on...

> Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5471    43945776   83  Linux
/dev/sda2            9824       10011     1510110    5  Extended
/dev/sda5            9824       10011     1510078+  82  Linux swap / Solaris

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/hdd: 17.0 GB, 17020329984 bytes
16 heads, 63 sectors/track, 32979 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       29064    14648224+  83  Linux
/dev/hdd2           29065       30056      499968   82  Linux swap / Solaris

Disk /dev/sdb: 127 MB, 127139840 bytes
8 heads, 32 sectors/track, 970 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         970      124112+   4  FAT16 <32M
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 2, 32)
Partition 1 has different physical/logical endings:
     phys=(968, 7, 32) logical=(969, 7, 32)
john@kubuntu:~$ 

sdb is an MMC/SD drive with a memory card in it.  hdd has slackware on it.

---

### Post by arnieboy on 2005-08-28
[QUOTE=arcanistherogue]I tried both hd1,0 and hd2,0, both said file not found.  lemme paste the results of the command you said, hold on...

 

sdb is an MMC/SD drive with a memory card in it.  hdd has slackware on it.[/QUOTE]
ok I got it. change it to (hd3,0) and it will work this time.

---

### Post by arcanistherogue on 2005-08-28
Eh... I tried both hd3,0 and hd0,0 this time...

i wonder what is wrong...

And I'm assuming hdd is hd1,0, as sda come up as hd2,0.  that must mean hdc comes up as hd0,0.

---

### Post by arnieboy on 2005-08-28
[QUOTE=arcanistherogue]Eh... I tried both hd3,0 and hd1,0 this time...

i wonder what is wrong...

And I'm assuming hdd is hd1,0, as sda come up as hd2,0.  that must mean hdc comes up as hd0,0.[/QUOTE]
No I am positive that hdd1 corresponds to (hd3,0) (Second hard disk on second IDE cable, first partition )
what do u mean u tried both hd3,0 and hd1,0. I hope u mean u tried them one after the other.
it has to be hd3,0.
please paste the contents of /boot/grub/menu.lst

---

### Post by arcanistherogue on 2005-08-29
Yes, I tried them seperately.  Here is the menu.lst : 

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Slackware 10.1
root		(hd3,0)
kernel		/boot/vmlinux-ide-2.4.29 ro root=/dev/hdd1
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by arnieboy on 2005-08-29
[QUOTE=arcanistherogue]Yes, I tried them seperately.  Here is the menu.lst :[/QUOTE]
ok dude lets try and solve this hd numbering problem once and for all.
from terminal type:
```
sudo grub
```
and press enter. when the "grub>" prompt comes. type this:
```
root (hd
```
**AFTER THIS DONT PRESS ENTER! PRESS TAB** and it will autocomplete and show you how grub recognizes your options.
u will get something like:
```
grub> root (hd
 Possible disks are:  hd0 hdX hd2
```
where X will stand for the number of hdd (where slackware resides). 
Now when the grub prompt (grub>)comes again type:
```
quit
```
grub will quit and u will return back to command prompt.

we already know from your menu.lst that grub is recognizing /dev/hdc as hd0 and /dev/sda as hd2. so we need the number of the third hard disk (where slackware resides) which u will get from here. whatever number u get, put that in the menu.lst file, save, exit and reboot!

---

### Post by arcanistherogue on 2005-08-29
> grub> root (hd
 Possible disks are:  hd0 hd1 hd2 hd3



its reading the Memory card as hd3 right?  I'm pretty sure, it comes up as sdb.

---

### Post by arnieboy on 2005-08-29
[QUOTE=arcanistherogue]its reading the Memory card as hd3 right?  I'm pretty sure, it comes up as sdb.[/QUOTE]
ur memory card and slackware are taking up hd1 and hd3 
but therez an easy way to find out what resides where.
do a 
```
sudo grub
```
again and at "grub>" prompt  type 
```
root (hd1,0)
```
This will tell u the filesystem type (if its "fat" u will know its ur memory card etc) and u will know what resides where.
the disk numbering convention of grub is pretty random. no real rules. hence /dev/sdb can come come up as hd1 which is really annoying.

---

### Post by arcanistherogue on 2005-08-29
Thats odd. When I did that, hd1,0 came up as ext2fs, when I swore I made it ext3.... 

Hmm...

---

### Post by arnieboy on 2005-08-29
[QUOTE=arcanistherogue]Thats odd. When I did that, hd1,0 came up as ext2fs, when I swore I made it ext3.... 

Hmm...[/QUOTE]
ext3 is just an ext2 filesystem with journaling enabled. thats why it gets listed as an ext2fs by grub.
add "savedefault" just before "boot" under the slackware listing in menu.lst and try again... let me know if it works and also the exact error in case it doesnt.

---

