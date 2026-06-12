---
title: "Something ate my GRUB!"
date: 2006-11-30
forum: General Help
---

### Post by jsteve54302 on 2006-11-30
Hi, all...  Not a pressing issue due to my setup, but I have following problem and would like to get it fixed:

I have a (sort of) triple boot system - ubuntu-ubuntu-xp, with xp on one physical drive and the two ubuntu's on the other.  I set up the system to have GRUB on both physical drives so that, if something goes horribly wrong on one, I can boot from the other.  The GRUB on sda (HD0, /dev/sdb1 on /boot) works fine, but the GRUB on sdb (HD1, /dev/sdb2 on /boot) keeps saying "Error 15: File not found" and refuses to use the menu.lst I modified on sdb (where it should look)...  worse, it keeps eating my entire GRUB directory on /dev/sdb2!  It's just gone...  Everything else is there...  just the GRUB's gone!  That partition pair even boots fine - from the other GRUB.  I've even tried restoring from the other installation's GRUB directory, and it just vanishes again.

So, my two questions are:
1:  What could be eating my GRUB like that?  (So I can prevent this happening in the future...)
2:  What can I do to drive off the little GRUB-eater now?

Thanks Everyone,

---

### Post by jsteve54302 on 2006-12-02
Well, whatever ate GRUB caughed it back up :)...  but I still can't get it to boot from my second hard drive by changing the boot order.  I get the GRUB menu (loaded from the second drive - the colors are different)OK, but when I select an item, it either can't find the file it points to or it can't mount the partition it's on...  I've tried every combination of device mapping/root devices I can think of...  I know I'm missing something blindingly obvious here, but I just don't see it.

So you have the info you need (i hope), here are the device.map and menu.lst for the 1st (working) drive and the second (not working, accessed by changing BIOS boot order):

1st device.map:
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
```
1st menu.lst:
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4d8608da-e80d-40fc-81de-d584c5dcd13a ro
# kopt_2_6=root=/dev/sdb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title        Ubuntu, kernel 2.6.17-10-generic Stable
root        (hd1,0)
kernel        /vmlinuz-2.6.17-10-generic root=/dev/sdb5 ro quiet splash
initrd        /initrd.img-2.6.17-10-generic
quiet
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode) Stable
root        (hd1,0)
kernel        /vmlinuz-2.6.17-10-generic root=/dev/sdb5 ro single
initrd        /initrd.img-2.6.17-10-generic
boot


title        Ubuntu Stable, kernel 2.6.17-10-generic TEST
root        (hd1,1)
kernel        /vmlinuz-2.6.17-10-generic root=/dev/sdb6 ro quiet splash
initrd        /initrd.img-2.6.17-10-generic
boot

title        Ubuntu Stable, kernel 2.6.17-10-generic (recovery mode) TEST
root        (hd1,1)
kernel        /vmlinuz-2.6.17-10-generic root=/dev/sdb6 ro single
initrd        /initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
root        (hd0,0)
makeactive
chainloader    +1
```

2nd (non-functioning) device.map:
```
(hd0)    /dev/sdb
(hd1)    /dev/sda

```
*NOTE:  I've tried both configuations here...

2nd (non-functioning) menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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


title        Ubuntu, kernel 2.6.17-10-generic TEST
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb6 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
boot

title        Ubuntu, kernel 2.6.17-10-generic TEST (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb6 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, kernel 2.6.17-10-generic Stable
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb5 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
boot

title        Ubuntu, kernel 2.6.17-10-generic Stable (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb6 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet
boot


# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
root        (hd1,0)
chainloader    +1


### END DEBIAN AUTOMAGIC KERNELS LIST

```

I really need to get this fixed because <off-topic type="windoze">I have to reinstall xp to get it to recognize the Audigy 2 ZS i just put in (yes i tried system restore)</off-topic> and I would really like to avoid GRUBbig from live cd...  Anybody have any ideas?

---

### Post by eriefisher on 2006-12-02
Why would you put GRUB on twice? Would they not conflict with each other.

---

### Post by jsteve54302 on 2006-12-02
I have two complete installations of Ubuntu - one that I reserve for "stable" operation("Stable"), and one for tinkering (that I can restore from an image on the stable installation if something goes horribly wrong - and it always does :) ) ("TEST").  The first GRUB boot loader is on hd(0) (grub notation), which also has my xp partition.  That's what I normally load from, but now I need to reinstall xp there because it's registry got hosed by me trying to install Creative sound drivers over the Realtek drivers, and now Creative refuses to play there -period- (forget nice).  That'll hose the GRUB on hd(0).  I want to be able to boot from the GRUB on hd(1), which has the linux partitions, by swapping boot order in the BIOS.  The setup looks something like this:

```
|+hd(0) = GRUB 0 (using Stable filesystem)
  |-hd(0,0) = winxp
  |-hd(0,1) = fat32 file transfer
|+hd(1) = GRUB 1 (using TEST filesystem)
  |-hd(1,0) 5GB on /boot (stable) (sdb1)
  |-hd(1,1) 5GB on /boot (TEST) (sdb2)
  |+hd(1,2) Extended, contains: 
    |-hd(1,4) 107GB on / (stable) (sdb5)
    |-hd(1,5) 107GB on / (TEST) (sdb6)
    |-hd(1,6) 8GB on swap (sdb7)
```hd(1,[3]), not having a primary partition to fill it, was piped to the bit bucket.  Since the GRUB on hd(0) uses hd(1,0)/grub for it's boot files, and the GRUB on hd(1) uses hd(1,1)/grub, they should be seperate from each other, and therefore no conflict (though both menu.lst's can (or at least did until the entire grub dir on hd(1,1) vanished yesterday and mysteriously reappeared today, but with a menu.lst that seemed unmodified from a clean install to hd(1,0),hd(1,4) boot any of the three OS's).  And since only one installation is running at any time, I can mount the other in, say, /mnt/linux<x> (and linux.boot<x> for /boot) where <x> is an arbitrary dsignation for the other installation), and fix any problems that preclude booting (or kill gdm) on the other partition a lot more easily.  By having two separate GRUBs, if one goes south I can use the other to recover.  And one's about to go south when I reinstall xp.  It's kind of like a crude, deliberately and thoughtfully asynchronized, hand-maintained version of RAID.

There are problems, of course, i.e. mount doesn't follow links/symlinks or mount points, but it should work pretty well...  _If_ I can get the GRUB on hd(1) working again so I can boot from hd(1), fix the nuked GRUB on hd(0), and switch BIOS boot order back...  Others in these forums have done it, usually posting about other problems, and I _did_ have it working...

 Oh, BTW, swap is not persistent, so using a single swap for both installations makes sense...

Yes, I could just GRUB by booting live from the Edgy install cd, but this way, I have minimal editing of the menu.lst file to point it in the right direction on both Ubuntus (as they are almost identical).  Besides, it's just more elegant.

Hope your question was answered somewhere in my prodigious verbiosity :).

---

