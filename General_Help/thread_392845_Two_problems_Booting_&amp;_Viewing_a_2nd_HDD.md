---
title: "Two problems: Booting &amp; Viewing a 2nd HDD"
date: 2007-03-25
forum: General Help
---

### Post by charish2k1 on 2007-03-25
Ok, so here's the deal... my computer went into a slight overheat and automatically shutdown while I was in Windows (I'm running a dual boot system). Let it cool down for a bit and booted it up again. Now I have two harddrives in my computer, a 250 GB as an all-purpose drive (also where Windows and Ubuntu live hatefully side-by-side) and a 20 GB (NTFS) where I keep all my music. 

While my computer was cooling down, I opened it up and fiddled around with it - I took my 20 GB harddrive and set it on the secondary IDE along with my DVD-RW drive. Now, Windows XP Pro can read the 20 GB drive just fine, but Ubuntu (6.10 is the version I'm running) won't pick it up. Originally, the 20 GB drive was labeled "hdb1" under the /home/charish/media folder. Now, the hdb1 in that folder is just a regular, empty folder. And so, I have no way to access my drive. 

So, I did a sudo fdisk -l and this was my output:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       22722   182514433+   7  HPFS/NTFS
/dev/hda2           30338       30401      514080    f  W95 Ext'd (LBA)
/dev/hda3           22723       30337    61167487+  83  Linux
/dev/hda5           30338       30401      514048+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2433    19543041    7  HPFS/NTFS

Judging by looking at that, I'm assuming the name of my 20GB got changed to hdd1. Now, question is, how do I get to access & view it again like it was before? (If it helps, it was read as /dev/hdb1 during my Ubuntu installation).

Whew, that was the first problem.... this second one is much simpler to explain. Also after the little overheat and self-shutdown and cool down, every time I try to boot into the regular Ubuntu kernel (latest one) from GRUB, it stays at that dos-like screen that says "Starting Up..." and hangs there; no error messages, nothing. Just hangs there. The only way that I can actually boot into Ubuntu is if I got into the recovery mode, enter in "exit" and let it load into Ubuntu from there.

Any help would be *much* appreciated. And thanks a lot for the help in advance folks =)

P.S. I know a little bit of coding, but not a whole lot so for sake of not making anyone frustrated (including myself) just explain all the coding and whatnot like one would to a newbie.

---

### Post by smokey edgy on 2007-03-25
It may be as easy as editing your /etc/fstab file and looking for /dev/hdb1 and switching it to /dev/hdd. But maybe it would be best to just try mounting it first. Open a terminal window and type in this:

mkdir test
sudo mount -t ntfs /dev/hdd test
sudo nautilus test

If you see a file browser showing the contents of your 20GB drive, then it should be ok to do the switch I mentioned above.

---

### Post by smokey edgy on 2007-03-25
Sorry not /dev/hdd but /dev/hdd1.

Hope that helps!

---

### Post by charish2k1 on 2007-03-25
Lo and behold that worked. I did both actually, lol (editting the fstab and mounting it). Still leaves the issue of the boot-up sequence hanging at that one point. Any ideas/suggestions/comments?

---

### Post by smokey edgy on 2007-03-25
charish, can you copy and paste the contents of the /boot/grub/menu.lst? Also,  I'm guessing this problem started to happen after your overheating issue?

---

### Post by charish2k1 on 2007-03-25
Surprisingly, it's been happening ever since I've installed Ubuntu... it used to be that it'd do this 1 out of every 3 times I booted into Ubuntu, but now it seems to be permanent that I have to go into recovery mode and boot into Ubuntu from there. Anyway, here's the contents of my /boot/grub/menu.lst:

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
# kopt=root=UUID=19931239-b535-4ae5-bbd8-f01095f77267 ro
# kopt_2_6=root=/dev/hda3 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by smokey edgy on 2007-03-26
I'm assuming there is no hard drive activity either, eh? I don't have much confidence with this but try temporarily removing the quiet and splash options in the section:

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

I have a feeling this is something lower level. The fact that it would work sometimes and not others suggests this. Not entirely sure why this would be. Not that this is the ideal solution, but have you reinstalled it before?

---

### Post by dcstar on 2007-03-26
> **charish2k1 said:**
> Ok, so here's the deal... my computer went into a slight overheat and automatically shutdown while I was in Windows (I'm running a dual boot system). Let it cool down for a bit and booted it up again. Now I have two harddrives in my computer, a 250 GB as an all-purpose drive (also where Windows and Ubuntu live hatefully side-by-side) and a 20 GB (NTFS) where I keep all my music. 

While my computer was cooling down, I opened it up and fiddled around with it - I took my 20 GB harddrive and set it on the secondary IDE along with my DVD-RW drive.
..........
   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2433    19543041    7  HPFS/NTFS

Judging by looking at that, I'm assuming the name of my 20GB got changed to hdd1. Now, question is, how do I get to access & view it again like it was before? (If it helps, it was read as /dev/hdb1 during my Ubuntu installation).
..........

Ubuntu identifies PATA drives thus:

/dev/hda - Primary IDE channel Master device
/dev/hdb - Primary IDE channel Slave device
/dev/hdc - Secondary IDE channel Master device
/dev/hdd - Secondary IDE channel Slave device

If you have moved the second drive from the Primary to Secondary channel then you will need to alter your /etc/fstab file to reflect the change.

---

