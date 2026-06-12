---
title: "Dual Booting 7.04 (currently installed) on IDE and XP on SATA"
date: 2007-07-03
forum: General Help
---

### Post by sgtcodex on 2007-07-03
Heya guys.

I've been using Ubuntu for a few months now, and despite the fact that I'm planning to dual boot, I absolutely love it.  I've never had a problem that lasted more than a few minutes, thanks to the incredibly powerful command line coupled with an easy to use desktop environment.

But I'm also interested in getting back into gaming.  Right now I've got a copy of UbuntuStudio 7.04 (if you don't know much about this, it's mostly the exact same as 7.04, with a few programs removed and a few added.) on an IDE hard drive.  Right next to me sits a SATA hard drive and a copy of Vista Ultimate and XP Pro (the original XP Pro, no service packs).  I want to install one of these on my computer (probably XP, but Vista if it works cleaner/easier), but I can't seem to find a tutorial that fits my current situation.

And FYI, I want to use grub to boot in the optimal situation, not a Windows boot loader.  Either way works if I have to, though.

---

### Post by tsav87 on 2007-07-03
I've never tried to dual boot from two separate CPUs, but I do know that on a single CPU dual boot, you will have to install windoze first and then install ubuntu. When installing ububtu, just pick the amount of space you want for your ubuntu partition and then install as normal, that will automatically set up a dual boot with Grub.

That's what I know about a single CPU dual boot, it may come in handing when trying to do a dual CPU dual boot.

---

### Post by tsav87 on 2007-07-03
on second thought...

You will have to use the windoze CPU as the primary, and the Ubuntu CPU as a slave drive.  Install windoze on the primary, then install Ubuntu on the slave.  If you do it in that order it SHOULD set up the dual boot with Grub.

Let me know how if goes.

---

### Post by smoker on 2007-07-03
hi, first off, you will probably need to find sata drivers for your xp/vista install, you can usually get these from the motherboard support website. you may have to also download a manual for your motherboard also.

depending on your bios and motherboard will depend how you can set your hard drives, and what will take priority as a master drive, eg, in my pc, i can set it to enable sata, but by doing so i have to disable one ide channel, so i can have the sata master, and the ide channel two will be slave, or i can set the ide one before sata, therefore an ide drive on that channel will be master, and the sata drive will be slave.

there are, of course, a host of different poosibilities, so i would recommend a motherboard manuel and maybe have a look at the options in your bios, to judge the best route to go.

hope some of this helps

ps - you could always have both windows and ubuntu on the sata drive, which will be slightly faster than booting from the ide, and use the ide drive for data, whatever,

---

### Post by sgtcodex on 2007-07-03
Sorry for the lack of system specs, guys.  Here they are:

Intel D865PERL Mobo
AGP ATI R420 (X800) Graphics Card
120 GB IDE with Ubuntu 7.04, Grub boot loader Hard Drive
1 GB of Memory
Dual core 2.6 GHz Intel Pentium 4 Processor

(yeah, it's an old PC.  Funny how something you put $1000 into building a few years ago can only be $300 now)

And I'm trying to install a SATA hard drive, put Windows on it, and dual boot the two if possible.  For reference, the manual for my motherboard can be found [here](ftp://download.intel.com/support/motherboards/desktop/d865perl/rl_English.pdf).

---

### Post by tsav87 on 2007-07-03
Make a full back-up of your Ubuntu install using Sbackup,

After doing that, you have two options.

1.  Format the IDE drive, install Windows, then install Ubuntu on the IDE drive as well, and use the SATA drive as a storage drive.

or

2.  Install the SATA drive as primary, IDE as slave.  Then install Windows onto the SATA drive, and then install Ubuntu on the SATA drive as well  and restore your Ubuntu install with the file you created with Sbackup.  And use the IDE drive as a storage drive.


If it was me, I would go with option two, just as long as you can connect the SATA drive to you motherboard, because the SATA drive will be faster.

---

### Post by koshari on 2007-07-03
i would disconnect the ubuntu drive and connect the sata, install xp, and then reconnect the ubuntu drive, 

then its just a manual tweak to the grub files to add the xp to the boot menu.

let me know if you need a walk throug, howerver there heaps of info ion it and the grub manual is very informative.

being a sata drive you will need to look into the device.map file as grub will need a translation of sda1 to hd1

---

### Post by sgtcodex on 2007-07-03
I'm a bit unfamiliar with sbackup, can someone tell me how to do a full system backup?

koshari, would that work -- do you know how to configure grub like that?  A tutorial would be quite helpful.  I'm going to need an idea of whether I should go with your way or tsav's way.

---

### Post by tsav87 on 2007-07-03
The default settings would be sufficient, just change the destination of the back up file to some where you can find it, like an external HD or thumb drive.'

When you have the new install of Ubuntu, just reinstall Sbackup and when you open on the Backup Restore GUI, just point it to the folder containing the backup file.

---

### Post by koshari on 2007-07-03
sure it would work, 

install the windows OS with the ubuntu drive disconnected first so it wont overwrite the grub MBR (even though this can easily be fixed anyway)

and post back,

---

### Post by koshari on 2007-07-03
> I'm a bit unfamiliar with sbackup, can someone tell me how to do a full system backup?

i use partimage to do partition backups and rsync to do data backups.
> 
You will have to use the windoze CPU as the primary, and the Ubuntu CPU as a slave drive. Install windoze on the primary, then install Ubuntu on the slave. 
tsav what are you talking about here, i see no reference in the initial op about running a virtual machine with multiple cpus! and sata drives have no master slave settings!

---

### Post by sgtcodex on 2007-07-03
Okay koshari, I'm going to trust you here because your way seems to better suit my needs.  I'll have to get back to you guys in a bit once I've backed up my ubuntu onto my "storage" PC (just in case I screw up, I'd hate to lose my Ubuntu) and installed windows.

---

### Post by koshari on 2007-07-03
thats why i would disconect the ide drive while doing the windows install, however its good practice to have a backup at any rate so it definitely wont hurt to do a backup, 

remember if your doing a partition backup you must conserve all file permissions ect..

---

### Post by sgtcodex on 2007-07-03
In the meantime, Koshari, can you tell me how to configure GRUB to do this, or post a walkthrough on the matter?

---

### Post by koshari on 2007-07-03
you will want grub files similar to mine, depending on your systems hd setup.

you wil want entry like this at the bottom of menu.1st

mine says hd0,0 but yours will differ depending on where the system sees the sata drive.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

gparted will tell you the hdd number, it will be likely sda1 (sata drive 1 partition 1)

then you will likely need a device.map file in /boot/grub to tell grub that sda1 is hd1,0

below is a copy of my /boot/grub/device.map file for reference
> 
(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/hdc
(hd3)	/dev/sda
(hd4)	/dev/sdb

---

### Post by tenshi-no-shi on 2007-07-04
I am stuck on this same problem, except for the fact that I am using all IDE drive, but there is the kicker, with my Motherboard all my drives are listed as sd*. Anyways here is what my grub/menu.lst file looks like.

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a010a65d-f603-4dd9-b001-83727d1958cf ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a010a65d-f603-4dd9-b001-83727d1958cf ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a010a65d-f603-4dd9-b001-83727d1958cf ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a010a65d-f603-4dd9-b001-83727d1958cf ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Keep in mind that it does not work. Here is the strange thing my device.map file looks like this.

```

(hd0) /dev/sda
(hd1)	/dev/sdb

```

And finally the REAL kicker... Here is the output of fisk -l. Keep in mind that I have 3 HDD two connected to the main IDE controller and one hooked up to my raid controller that is set in IDE mode.

```

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   c  W95 FAT32 (LBA)
/dev/sda2            9965       19929    80043862+   f  W95 Ext'd (LBA)
/dev/sda5            9965       19929    80043831    b  W95 FAT32

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1824    14651248+  83  Linux
/dev/sdb2            1825        4982    25366635    5  Extended
/dev/sdb5            1825        4742    23438803+  83  Linux
/dev/sdb6            4743        4982     1927768+  82  Linux swap / Solaris

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7475    60042906    7  HPFS/NTFS

```

Know keep in mind that the first one is the storage drive that used to be slaved to my Ubuntu Drive and set up as sdb but now is the master on the raid controller and say it's sda. My Ubuntu drive is now sdb and my windows drive that is the slave to my ubuntu drive is sdc.

Okay that is it... Please help. can I get this to work, or am I going to have to go bad to switching them manually by disconnecting my ubuntu one, and connecting my windows one, which at this point seams like the best option... hmm maybe I should get a hdd bay that I can do that will... Hmmm.. Anyways help wold be appreciated.

Edit: P.S. the first drive actually has one Fat32 partition one Ext Partition so I don't know why it says I have two Fat32.

---

### Post by sgtcodex on 2007-07-04
Well, when I go into gparted, I only get a gui interface, but here's what I can figure from it:

/dev/sda (contains ubuntu)
/dev/sda1 -- ext3
/dev/sda2 -- extended
     /dev/sda5 -- linux-swap

/dev/sdb (contains windows)
/dev/sdb1 -- ntfs
and a couple megs of unallocated space.

But I'm really not sure how to go from here.  Do I just open my device.map and change
```

(hd0)	/dev/sda
```
to
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

and make my menu.lst say

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by mattyrigby00 on 2007-07-04
just install xp to a different partiton then use the live cd to re install grub

---

### Post by sgtcodex on 2007-07-04
I'm sorry, but at this point, I'm not interested in changing course.  All I have to do is figure out the correct numbers to use in my menu.list and device.map and I'll be fine.

---

### Post by koshari on 2007-07-04
those numbers look good to me and should work.

let me know if they dont, 

btw at boot time you can edit any of the entrys for single boot, this is handy if you want to try a different hd?.? combination . however it will only try it for that boot and wont save to the menu.1st file. you still have to do that manually.

also you will obviousely need root permissions to edit /boot/grub/menu.1st and /boot/grub/device.map .

if you have any error codes post them here, 13 and 21 are the usual suspects,

---

### Post by koshari on 2007-07-04
tenshi-no-shi  what is the actual error do you get?

---

### Post by tenshi-no-shi on 2007-07-13
Sorry I have been busy with other things and have just gotten back to this. My problem is that the grub is not recognizing my windows drive. Is there some way that I can reinstall grub so that it sees them all?

---

