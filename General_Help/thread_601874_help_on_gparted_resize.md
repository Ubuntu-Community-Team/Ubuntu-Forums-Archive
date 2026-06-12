---
title: "help on gparted resize"
date: 2007-11-03
forum: General Help
---

### Post by g.a. on 2007-11-03
Hi,

my current partition is shown in the attach. I would like to switch 10 GB from the ntfs partition (that contains winxp) to the ext3 partition (kubuntu 7.04) without loosing the used space of both the partitions.

It seems that this is possible with gparted. However, having read the documentation it is not clear to me how to practically proceed.  shall I first resize (decreasing) the ntfs partition, test if this was successful and then resize (increasing) the ext3 partition? shall I do both the operations at the same time? shall I just increase the size of the ext3 partition?

it is clear to me that a backup just before partitioning is mandatory but... if something fails what could be the effects?

thanks in advance,
g.

---

### Post by khughitt on 2007-11-03
Heya,

You should be able to do both steps without having to reboot and with little risk. Just to be safe, I would backup any absolutely critical files, but the chances of anything bad happening are slim.

What you will want to do then is first login to Windows, and check the disk for any errors.. Sometimes if windows has not shut-down properly, there will be errors with the journal system that will prevent you from resizing the partition. To force a check you can right click on the hard-drive from explorer, and go to properties. There should be an option under one of the tabs there to perform a disk-scan.

Next use either gparted or gparted live! and right click the windows partition and choose "resize." Tell it what size you want it to use. Then do the same for the ext3 drive and add the free space it now shows available to it. Afterwards hit "ok" or "start" or whatever the option is, and it should perform both steps.

If you have any trouble, feel free to post here again :)

Goodluck!

---

### Post by g.a. on 2007-11-05
well, yes, I need further help...

I made the check on the ntfs partition (it tooks a while...) and run gparted. most of the commands are disabled. in the documentation i can read the following

------------------
5 : Why are some menuitems disabled?
1. The partition is mounted and modifying a mounted partition is DANGEROUS. Just unmount the partition or in case of swap, disable it.(use swapoff)

2. At startup gparted decides which operations on which filesystems are supported. For instance, to create an ext3 filesystem gparted needs mkfs.ext3. If this cannot be found on your system, the creation of an ext3 filesystem is not possible and therefore disabled in gparted. The same goes for copy, resize etc.. 
----------------

shall i umount both the ntfs and the ext3 partition before resizing both? does it mean:

> umount /media/sda2  (the ntfs partition)
> umount /                   (the ext3 partition)

and then run gparted and resize?

thanks
g.

---

### Post by khughitt on 2007-11-05
Try using [Gparted live! ]("http://gparted-livecd.tuxfamily.org/")instead, then you should be able to modify your / partition as well.

---

### Post by g.a. on 2007-11-05
you mean that i should be able to resize the partitions without unmounting them?

thanks,
g.

---

### Post by khughitt on 2007-11-05
> **g.a. said:**
> you mean that i should be able to resize the partitions without unmounting them?


No, I meant that you should use the bootable Gparted live cd instead, in which case you none of your hard-disk partitions would be mounted, and therefor resizing should not be a problem.

I'm not sure whether you can resize a partition while it is mounted. I have never tried, but since it seems that gparted would not let you, this means that you *cannot* do it.

Sorry if I wasn't clear before. Does this help?

---

### Post by g.a. on 2007-11-05
still not solved my problem.

i tried both:

1) from gparted live it starts doing some operation correctly (calibrate, calculate new size, check filesystem) and experiences an error when doing shrink filesystem, in detail in:

ntfsresize -P --force --force /dev/hda2 -s 15792537599 --no-action

2) from gparted "on site" i had to unmount the ntfs partition from shell, then it starts the resize and stops in the same point. in this case however, i could save the log file.

I'm copying the only failed operation. it says to try freeing less memory, i have not tried yet...

best,
g.


resize the filesystem    ( ERROR )
     	
run simulation    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda2 -s 15784378368 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 26320892416 bytes (26321 MB)
Current device size: 26320896000 bytes (26321 MB)
New volume size : 15784374784 bytes (15785 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 11684 MB (44.4%)
Collecting resizing constraints ...
Needed relocations : 760352 (3115 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1360 > 1024), not yet supported!
Please try to free less space.

---

### Post by g.a. on 2007-11-05
well, yes, i just resized of 5 Gb instead of 10 Gb and it worked fine!

in order to maximise the possibility of troubles I made the ntsf resize with gparted and the ext3 resize with gparted live.

I'm testing the linux stuff and they are ok, i have tested yet the winxp.

bye
g.

---

