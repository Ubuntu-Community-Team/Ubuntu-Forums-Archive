---
title: "Dual Booting Issue"
date: 2007-09-06
forum: General Help
---

### Post by Harkainos on 2007-09-06
Ok....

I started with a fresh drive, fresh install on Windows XP Pro - during installation i partitioned the drive to have a small portion as ntfs and the rest unpartitioned. All worked great there...

I installed ubuntu 7.04 to the Unpartitioned space and now I can't load Windows. Ubuntu works fine, but I can't get Windows to load. It is in the Grub and the menu is there but when I select it all I get is a black screen with:

Starting Up...

Written on it. Any Ideas. Any pros to this, what steps did you take? How did you partition the drive?

---

### Post by Russty of Oz on 2007-09-06
I have had similar problems in the past and found that Super Grub is great for fixing some booting problems.   You can tell it to fix the windows boot loader. I am not saying that this WILL solve your problem but it is something to try. [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by thelocust on 2007-09-06
Post your output for **sudo fdisk -l** in terminal. And your /boot/grub/menu.lst file. By the way Super Grub Disk is a life saver but if you don't want to download it and burn it your probably dealing with a pretty easy fix, but I would suggest having a copy available anyways. It's kinda hard t burn a disk when your computer won't start.

---

### Post by Harkainos on 2007-09-06
I will post the output around 630 central time. I am at work right now and have no access to that system.

:/

---

### Post by Harkainos on 2007-09-06
Here are the outputs


**fdisk -l**

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1524    12241498+   7  HPFS/NTFS
/dev/sda2            1525        3348    14651280   83  Linux

**Grub Menu**

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
# kopt=root=UUID=dfdcede1-d431-4941-b408-db7f2177e1d6 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dfdcede1-d431-4941-b408-db7f2177e1d6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dfdcede1-d431-4941-b408-db7f2177e1d6 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=dfdcede1-d431-4941-b408-db7f2177e1d6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=dfdcede1-d431-4941-b408-db7f2177e1d6 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I hope this will help us find the problem.... Meanwhile I will check out super grub

---

### Post by merlinus on 2007-09-06
Looks pretty good to me.  You might change root to rootnoverify in the windows stanza -- it might help.

Also noticed that no swap partition exists.  Did you do this on purpose?

You might try reinstalling grub, which you can do from ubuntu.

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

Probably will be root (hd0,0) and setup (hd0).

Also change #groot in /boot/grub/menu.lst to (hd0,0).  This may be indicate the problem is that grub got installed to the ubuntu partition rather than the mbr.

-merlin

---

### Post by Harkainos on 2007-09-06
Nah... I tried to do the partition manually during Ubuntu Install... I think that is where my problem is. I will try this and run Super Grub - Otherwise it is a fresh start, again.

---

### Post by rsambuca on 2007-09-06
> **merlinus said:**
> Looks pretty good to me.  You might change root to rootnoverify in the windows stanza -- it might help.

Also noticed that no swap partition exists.  Did you do this on purpose?

You might try reinstalling grub, which you can do from ubuntu.

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

Probably will be root (hd0,0) and setup (hd0).

Also change #groot in /boot/grub/menu.lst to (hd0,0).  This may be indicate the problem is that grub got installed to the ubuntu partition rather than the mbr.

-merlin

I agree with everything except for the last part.  I would leave the groot as it is since it refers to your ubuntu partition.

---

### Post by merlinus on 2007-09-06
Yes, now that I think about it, leave #groot alone.

Thanks!

-merlin

---

### Post by thelocust on 2007-09-06
Am I crazy or is there no Swap Partition?

---

### Post by Harkainos on 2007-09-06
YES.... there is no swap partition...

And that is probably what is causing this. I suppose I could 'reinstall' ubuntu and format everything... maybe

---

### Post by Harkainos on 2007-09-06
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

I know that this has been # out and not active, but would it help to activate it?

---

### Post by merlinus on 2007-09-06
It is already active, even though there is a # at the beginning of the line.

It is something that is read whenever there are kernel upgrades.

Also, you might try supergrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

And it would be easy to shrink your ubuntu partition by about 1.5G and create a /swap partition without reinstalling.

-merlin

---

### Post by Harkainos on 2007-09-06
I have gparted and a ton of unallocated space. I would be happy to create a /swap partition...


Could you give me a simple walk through on how to do that?

I tried the steps above and they didn't work. I did 'clean' up the grub menu, so there weren't so many flipping options. 

I downloaded the Super Grub, but when I startup with it I go through the options and it gives me and error 15...

---

### Post by merlinus on 2007-09-06
You will need gparted live cd in order to shrink your ubuntu partition.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Were you able to boot windows with supergrub, following the directions at the link in my last post?

-merlin

---

### Post by Harkainos on 2007-09-06
No... when I selected the 'Boot Windows' Option it showed a black screen

Rootnoverify (hd0,0)
chainloader +1

Etc....

Now, if I select the 'Repair windows boot' that will erase the grub, correct?

---

### Post by merlinus on 2007-09-06
Yes, but then you can reinstall it.

-merlin

---

### Post by Harkainos on 2007-09-06
So.... here I am.. in Windows. I have partition magic... so I am going to run that and nuke the ext3/unallocated partition tables

Then reinstall Ubuntu

Wish me luck.

---

### Post by merlinus on 2007-09-06
No, no, no!  Use gparted live, NOT partition magic.  It will really screw things up!

-merlin

---

### Post by merlinus on 2007-09-06
And you do not have to reinstall ubuntu, unless you prefer to do it that way.

-merlin

---

### Post by Harkainos on 2007-09-06
lol doh... i did it already

basically I have my OS on like 11gb

Then I have unpartitioned space on the rest... I figure I could start from scratch.

---

### Post by merlinus on 2007-09-06
Give it a try,  You might want to create a separate /home partition, in addition to / (root) and /swap.That way your settings, preferences, configurations, email and bookmarks can survive a reinstall or upgrade.

In tact, best to create an extended partition, and then create logical partitions within that.  It will offer lots more flexibility.

If you run into trouble, post back.

-merlin

---

### Post by Harkainos on 2007-09-07
Still didn't work.... here is the new Fdisk/menu.lst


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1807    14514696    7  HPFS/NTFS
/dev/sda2            1808       29644   223600702+  83  Linux
/dev/sda3           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris


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
# kopt=root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
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
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


I changed the root to rootnoverify as described above... still not loading.

---

### Post by merlinus on 2007-09-07
> 

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


I immediately see that you should delete:

title		Other operating systems:
 root

-merlin

---

### Post by Harkainos on 2007-09-07
I deleted the text above and still no go... here is the new list.  root and rootnoverify in the windows load have the same result....



title		Ubuntu Fiesty
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu Fiesty (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by merlinus on 2007-09-07
You could try that, and might as well put the other lines just deleted back in.

If that does not work, then at this point I would use supergrub (or your xp cd) to restore its bootloader to the mbr, and then reinstall grub.

-merlin

---

### Post by Harkainos on 2007-09-07
What steps would I need to take to reinstall grub?

---

### Post by merlinus on 2007-09-07
```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

It will probably be root (hd0,1) and setup (hd0).

-merlin

---

### Post by rsambuca on 2007-09-07
> **merlinus said:**
> ```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

It will probably be root (hd0,1) and setup (hd0).

-merlin

This information MAY work in some cases, but if the user has more than one hard drive, it will not necessarily work.  Merlinus, I see you have been helping others quite a bit with this, which is great, but make sure you are careful to watch for the particulars of the user's setup.  There have been a few people that you have given this information to when it didn't apply, because the setup command should have been directed to a different drive.

---

### Post by merlinus on 2007-09-07
Thanks for the heads-up, rsambuca.  I already had thanked you previously for pointing this out.

But in this case, Harkainos has only one hdd, as far as I can tell.

OTOH, I could simply refer people with this problem to you.

;)

-merlin

---

### Post by Harkainos on 2007-09-07
I have one 250gb hard drive.

During the Windows XP install I partitioned the hdd off with 12gb (ntfs) and rest (unpartitioned)

Then I installed Ubuntu - My intent was to put Ubuntu on 15gb of the unpartitioned space (creating the ext3/swap portions) and then format the rest (unpartitioned) to NTFS again and have Ubuntu with read/write capabilities to the NTFS drive....

That is currently how it is setup. Please lemme know what changes need to be. Would it still be (hd0,1)?

---

### Post by merlinus on 2007-09-07
What does this show?

```

sudo fdisk -l

```

Also, when you ran the grub commands, what did you get for find?

-merlin

---

### Post by Harkainos on 2007-09-07
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1807 14514696 7 HPFS/NTFS
/dev/sda2 1808 29644 223600702+ 83 Linux
/dev/sda3 29645 30401 6080602+ 5 Extended
/dev/sda5 29645 30401 6080571 82 Linux swap / Solaris

---

### Post by merlinus on 2007-09-07
From what I can see (and our calgary friend may disagree), to reinstall grub, do this:

sudo grub

-- to get to the grub shell

Then:

root (hd0,1)
setup (hd0)
quit

Then restart and see what happens.

-merlin

---

### Post by rsambuca on 2007-09-07
Looks good to me!

---

### Post by merlinus on 2007-09-07
Thanks!

And just for the record, I have learned lots from reading your posts.

-merlin

---

### Post by Harkainos on 2007-09-07
Once I repair the MBR for windows, how would I run that command.... considering I wouldn't have access to terminal (only CMD)?

---

### Post by merlinus on 2007-09-07
Does the grub menu now appear on bootup?  If so, post:

```

cat /boot/grub/menu.lst

```

after booting into ubuntu.

-merlin

---

### Post by Harkainos on 2007-09-07
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro

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

## ## End Default Options ##

title           Ubuntu Fiesty
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu Fiesty (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=74dac547-6202-4a27-b03b-289db3859ae3 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by merlinus on 2007-09-07
Looks good to me, but of course, it did before as well.

Is Windows an option in the grub startup menu?  Or only ubuntu?

-merlin

---

### Post by Harkainos on 2007-09-07
Yeah... it is available in both Super Grub and normal menus.

---

### Post by merlinus on 2007-09-07
So what happens when you select windows in the grub menu?

And if that does not work, can you boot into it via supergrub cd?

-merlin

---

### Post by Spymaster101 on 2007-09-07
Sorry to interupt the Converstion but when you guys say to edit the menu.list or whatever, how do you do that?

when i try to do that it says it is a read only file.

---

### Post by merlinus on 2007-09-07
It would have been better to start a new thread with your question, but....

```

gksudo gedit /boot/grub/menu.lst

```

If you are going to play around with it, best to make a backup copy first.

```

cp /boot/grub/menu.lst /boot/grub/menu.lst_old

```

Then if you mess up, you can restore it.

-merlin

---

### Post by Harkainos on 2007-09-08
In both super grub and grub menu when I select windows it goes to a black screen and says:


Starting Up...
_




This has always been.

---

### Post by merlinus on 2007-09-08
At this point, I wonder if your windows partition isn't borked, because supergrub is excellent at booting other operating systems.

You can backup data and reinstall xp to its existing partition, and then reinstall grub.

If you are going in that direction, then nothing would be lost by restoring xp to the mbr.  Boot from xp cd, select recovery, and then fixboot (or fixmbr).

-merlin

---

### Post by Harkainos on 2007-09-08
All my data is on an external ext3 drive... so I am not worried about data loss.... I simply want to run both OS's

Really here is my goal. Have a windows and ubuntu partition where they share data from a 3rd partition (preferably ntfs format)

I will dl the gparted bootable and rewipe everything.... This probably won't be complete til monday... wish me luck. 

@ Merlin - you have been a great help in this. I will report back on Monday. If you could keep your eyes open for me that would be amazing.

---

### Post by merlinus on 2007-09-08
Atr this point, it is probably easier to start over, as long as your data is safe.

Be sure to install xp first, however, in a primary partition.

You can use gparted live to set up the partitions beforehand.  

You might consider creating an extended partition for both ubuntu, its swap file, and the shared data partition, as that will give you more flexibility going forward.

Good luck!

-merlin

---

### Post by highgeere on 2007-09-30
Hey, I hate to open this back up after 3 weeks, but this is not an isolated issue. I have seen this exact issue on two PCs that I have installed 7.04 on. The process I take when installing is the same as well:
- create smallish ntfs partition and install XP
- partition the remainder of the drive manually during the Ubuntu install
Everything seems fine, except selecting XP from the grub menu gets me "starting up ..." and nothing else. This exact process worked on my own PC, but I used the alternate installer rather than the liveCD/installer. I have attempted to use SGD to reinstall grub with no success. I know the XP installation is still good because I can run fixmbr from a recovery console and boot windows no problem. I can then reinstall grub and boot ubuntu no problem. Never both though. Does this make sense to anyone else?

---

