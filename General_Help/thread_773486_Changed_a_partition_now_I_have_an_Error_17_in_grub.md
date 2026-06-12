---
title: "Changed a partition now I have an Error 17 in grub"
date: 2008-04-28
forum: General Help
---

### Post by jibuntu2 on 2008-04-28
I have a dual boot setup. with Windows XP on /dev/hda1 and Ubuntu is on /dev/hda2 with the swap on /dev/hda5 under /dev/hda3. Im using an HP notebook that had a 11 gig system partition with restore data on it. I think that was /dev/hda4. I also had about 800 megs of unpartitioned space.

I deleted the restore/hp partition in Windows XP with disk manager and then made a new partition combined with the free, unused space. I then encrypted it with truecrypt because I wanted to check that out.

Now when I reboot I get this in grub:

Error 17

and Grub doesnt even display a menu. Im using a live cd to post this.

PLEASE help! Im a linux noob and I dont know how to get it going again.

---

### Post by jibuntu2 on 2008-04-29
anyone even know what Error 17 means? This sucks.

---

### Post by Arwen on 2008-04-29
I can't help you out cause you mentioned sth about truecrypt (I don't know much about encryption and stuff) but error 17 means that a partition can't be mounted for some reason.You can use [GAG]("http://gag.sourceforge.net/") to boot in your ubuntu or [SuperGrubDisk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17")
As far as I know you have to delete the two entries of /boot/grub/menu.lst that correspond to the partitions you created and add a new entry for the new one.
Anyway,you'll have to fix your grub somehow,I suggest waiting for a more precise answer.
Good luck :-)

---

### Post by jibuntu2 on 2008-04-29
Thanks for the info! I have no idea how to edit grub though. Its just the menu.lst file under boot right? Dont I have to recompile grub after I change the lst file? How do I recompile if so?

---

### Post by Zyphrexi on 2008-04-29
editing menu.lst

```
sudo gedit /boot/grub/menu.lst
```

substitute gedit for your favorite text-editor. (i like gedit)

I don't know much about truecrypt, having never heard of it before, but if you removed the partition that had grub installed on it, that could be a problem.

I actually did one better than you, and accidentally deleted my /boot, so this isn't a big deal.

/dev/hda1 should translate to hd(0,0) in grub, and /dev/hda2 being hd(0,1)

check out your menu.lst and make sure that's right, or did you completely delete your windows partition? (is /dev/hda1 gone?)

---

### Post by confused57 on 2008-04-29
Here's a description of grub error 17:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

You might want to open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

You could try reinstalling grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you still can't boot, then try mounting your root partition, using the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda2 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
```

Just encrypting a separate partition with truecrypt "shouldn't" affect your ability to boot(error 17).

---

### Post by jibuntu2 on 2008-04-29
Thanks so much for the help - my linux partition is hda2, windows is 1, and they both read fine from the live cd. Grub wasnt on the partition I erased im pretty sure - although grub did have the partition as bootable that I got rid of. I can still see it in the menu.lst. I bet I could fix it if I removed that entry and recompiled grub. can I just fix the menu.list and then do a grub-install or something? thanks@!

---

### Post by Zyphrexi on 2008-04-29
yeah just do that grub-install thing, I usually have to look it up myself. but i don't see why you'd need to recompile grub.

I'd do a grub-install just to be safe, then have it update your partitions and whatnot. there should be a howto around here somewhere, just not totally sure...

it sure would be nice if they included some of the tuts in a default install.

---

### Post by jibuntu2 on 2008-05-02
Sorry for the delay but thanks for helping - im on the road which makes this even more troubling.

heres my fdisk -l

> 
/dev/hda1   *           1        7073    56813841    7  HPFS/NTFS
/dev/hda2            7074        8538    11767612+  83  Linux
/dev/hda3            8539        8609      570307+   5  Extended
/dev/hda4            8610        9729     8996400    7  HPFS/NTFS
/dev/hda5            8539        8609      570276   82  Linux swap / Solaris


heres my menu.lst. I can read all of the partitions fine from a live cd:



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
# kopt=root=UUID=4793f829-7590-404b-8b49-f67fde2587a6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4793f829-7590-404b-8b49-f67fde2587a6 ro quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4793f829-7590-404b-8b49-f67fde2587a6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4793f829-7590-404b-8b49-f67fde2587a6 ro quiet
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4793f829-7590-404b-8b49-f67fde2587a6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


---

### Post by confused57 on 2008-05-02
With Ubuntu on /dev/hda2, your root should be (hd0,1):
```
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=4793f829-7590-404b-8b49-f67fde2587a6 ro quiet
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```

You could try mounting your root partition with the live cd & changing it:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

If you tried reinstalling grub with the live cd, what did "find /boot/grub/stage1" show?

If you have access to another computer, you might want to try boot Windows &/or Ubuntu with Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by jibuntu2 on 2008-05-04
Thank you! Super Grub Disk got me back into my OS. Im hesitant to use it to fix it, because it doesnt seem to want to set it so grub dual boots - it seems to want to either set it to either windows OR linux, but not both. Great program though. Thank you all.

---

