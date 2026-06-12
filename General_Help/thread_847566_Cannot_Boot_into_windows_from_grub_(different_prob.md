---
title: "Cannot Boot into windows from grub (different problem than the other thread)"
date: 2008-07-02
forum: General Help
---

### Post by jumponskis on 2008-07-02
here is my results for 'sudo fdisk -l'
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         967     7310488+   c  W95 FAT32 (LBA)
[COLOR="Blue"]/dev/sda2   *         968       18428   132005160    7  HPFS/NTFS[/COLOR]
/dev/sda3           18429       20673    16972200    5  Extended
/dev/sda5           18429       20573    16216168+  83  Linux
/dev/sda6           20574       20673      755968+  82  Linux swap / Solaris

```


The highlighted partition is my C: drive which is windows XP. I've used supergrub and it worked fine and fixed the grub menu but I still cannot open windows. If I choose windows from the grub menu It just hangs like it did before. Windows is on the second partition only because the first is a recovery partition than I would just as well not have If I was able to modify it which I am not. What happened was that one day I accidentally chose the recovery partition in grub listed under other os's (windows me/2000/xp) when the correct selection was Windows XP home.  As I see the recovery screen appear and a message stating that it was starting formatting and all data on the c: drive would be returned to factory settings (s-s-SAY WHAT?!), I used the switch at the back of my computer to immediately shut off the computer and halt microsoft(-in-the-head)'s evil plot to force me to format all my beloved files (song, movies, essays, and pretty much everything else important in my life). As soon as someone can help remedy my actions (stupid hard shut-off, why are you so brutal to my computer) I can promptly start perusing the forums for a way to delete hp(ea-brain)'s stupid f*****g recovery partition. What an awful invention. More like data-loss partition.


No I can't mount the correct partition with manual mount, auto mount, or with supergrubdisk livecd. I tried it with the supergrub cd and it says that the filesystem type (e.g. ntfs, nts, FAT32 etc...) is unknown. I believe this is the problem but I have yet to come across something that will let me edit the file system type.  I've tried gparted, supergrub livecd, normal grub commands in terminal, ntfsprogs, testdisk, god I CANNOT LOSE 160GB OF MUSIC MOVIES AND HOMEWORK ALLRIGHT I CANNOT KEEP MY COOL ANYLONGER SOMEONE HELP ME BEFORE I START GOING CRAZY!

any help from real forum veterans would be greatly appreciated

---

### Post by jimv on 2008-07-02
Ok, need a few things:

Need the output of these commands:

```
cat /boot/grub/menu.lst

sudo mkdir /media/test

sudo mount /dev/sda2 /media/test

ls /media/test
```

---

### Post by jumponskis on 2008-07-02
cat /boot/grub/menu.lst:


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
# kopt=root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

sudo mkdir /media/test:

didnt do anything...except ask for my password to use the sudo command.... and create a folder called test in my filesystem/media/ folder

sudo mount /dev/sda2 /media/test:

```

Record 6 has no FILE magic (0x0)
Failed to open inode: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```
the same message I get when I try to mount it the easy way (by selecting it in the places menu)

ls /media/test:

nothing.  nothing happened at all.

---

### Post by jimv on 2008-07-02
Try this:

```
sudo apt-get install ntfsprogs

sudo ntfsfix /dev/sda2
```

Then try mounting the drive again.

---

### Post by jumponskis on 2008-07-02
i've already tried this.  any other suggestions.  besides the ones I listed.

---

### Post by jimv on 2008-07-02
My mistake, I missed that you tried ntfsfix.

---

### Post by jumponskis on 2008-07-05
so does noone have any ideas on how to recover a corrupt NTFS partition?

bump

---

### Post by caljohnsmith on 2008-07-05
> **jumponskis said:**
> so does noone have any ideas on how to recover a corrupt NTFS partition?

bump
Well, if ntfsfix didn't work, another choice would be to try and fix things from a Windows angle--do you have your original Windows CD? You could boot that up and first do a "chkdsk" on your Windows partition, and then a full Windows repair. If you don't have a Windows CD, you might check out the "Ultimate Boot CD" as it has lots of useful tools that will help you recover your Windows partition (see utimatebootcd.com).

---

### Post by sea_monkey987 on 2008-07-07
I'm guessing you didn't read this since you didn't respond in the other thread:

Try photorec:
[http://lifehacker.com/software/data-...rec-161318.php](http://lifehacker.com/software/data-...rec-161318.php)

Unlike what its name implies, it recovers any document.
Quote:
Photorec ignores the filesystem, this way it works even if the filesystem is severely damaged.
From what I can see, it should be on the testdisk livecd. I know for sure that it is in the ubuntu repositories. Install the "testdisk" package and then do sudo photorec from the terminal (from the livecd obviously).

---

### Post by jumponskis on 2008-07-14
> **sea_monkey987 said:**
> I'm guessing you didn't read this since you didn't respond in the other thread:

Try photorec:
[http://lifehacker.com/software/data-...rec-161318.php](http://lifehacker.com/software/data-...rec-161318.php)

Unlike what its name implies, it recovers any document.
Quote:
Photorec ignores the filesystem, this way it works even if the filesystem is severely damaged.
From what I can see, it should be on the testdisk livecd. I know for sure that it is in the ubuntu repositories. Install the "testdisk" package and then do sudo photorec from the terminal (from the livecd obviously).
 
yes i did try this.  It would work if I had another 160GB partition to write to....

---

