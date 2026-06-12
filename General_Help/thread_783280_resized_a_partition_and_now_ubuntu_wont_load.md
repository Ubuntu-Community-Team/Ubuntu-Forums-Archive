---
title: "resized a partition and now ubuntu wont load"
date: 2008-05-05
forum: General Help
---

### Post by konradpiskorz on 2008-05-05
I switched over to ubuntu only a couple weeks ago, my first linux distro.  It has been a pleasent experience but I made the mistake of leaving a 10gig NTFS partition in case I felt like dual booting windows.  I never did install windows and decided to remove the partition and extend an empty ext3 partition over it.

Anyways, my original HD partition was something like this (approximate gigabyte sizes)
main  18 gigs ext3
swap 2 gigs
storage 70 gigs
win 10 gigs NTFS

I wanted to combines the 70gigs ext3 in storage with the 10 gigs NTFS to one 80 gig ext3 partition.


I loaded up kubuntu live and used QTparted to do this.

Now heres where I made a big mistake.  QTparted labeled the drive as busy even though it wasn't mounted.  I'm assuming this has something to do with it being my laptop drive.  It changed the partition after I said ok assuming it only mattered if it was mounted.  And when I rebooted... ubuntu wouldnt load.  What would happen is this:

The regular bios stuff would happen as expected, it would then attemp boot up as:

> Intel(R) Boot Agent GE v1.2.30
Copyright (C) 1997-2005, Intel Corporation

Initializing and establishing link...

It hangs at this screen for a solid 30 seconds...  Maybe more then continues on and shows this

> Intel(R) Boot Agent GE v1.2.30
Copyright (C) 1997-2005, Intel Corporation

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent.
GRUB Loading stage1.5.

GRUB loading, please wait...
Press 'Esc' to enter the menu... 1

After this a screen FLASHES for half a second then goes blank.  I had to break out the digicam to snap a pic to read what it said.

> Starting up
[   71.207730] PCI: BIOS BUG #81[49435000] found
[   71.295232] 00.0a : SCMf010 not responding at SIR 0x2f8. conf
iguring
[   71.299604] 00:0a : responds at SIR 0x2f8, FIR 0x6f8
Loading, please wait...
_

And then a black screen.  Now I figured either my MBR or partition table is buggered.  However when loading from ubuntu or kubuntu live CD's the file system and all its contents appear intact and accessible.

PXE-E61 error appears to be a boot up hard disk error.  The cable can be ruled out as a Live cd can access the hard drive just fine and the HD is perfectly accessible on an external USB-SATA cable.


sudo fdisk -l returns this
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 *512 = 8225280 bytes
Disk identifier: 0x0c710c70

   Device Boot  Start    End    Blocks  Id  System
/dev/sda1   *       1   2415  19398456  83  Linux
/dev/sda2        2612  12161  76710375  83  Linux
/dev/sda4        2416   2611   1574370  82  Linux swap / Solaris

Partition table entries are not in disk order

My fstab file reads
> union / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda4 swap swap defaults 0 0

Essentially, I want to know if it is possible to save my settings, installations and everything in my ubuntu without having to go for a clean HD wipe and reinstall.  I've spent the past two weeks of my life setting up ubuntu, a debian etch server and learning linux and I'm just about the end of my computer rope.

I just don't want to have to go through remembering everything I installed, changed and downloaded to get the desktop the way i wanted it.

I thought that maybe copying the entire file system using dd, and then pasting it over a fresh install would work, although I'm reluctant to try it as it'll probably just cause the problem to resurface.  Is there a way, I can simply find out everything I've downloaded, installed etc.  IE any changes from a fresh ubuntu install.  Or even better yet can I fix my hd so it'll just boot ubuntu?

Oh yes and I'm running
Ubuntu 7.10 - Gutsy Gibbon
Toshiba Tecra A6 (Laptop)

Thank you very much,
Konrad Piskorz

Also of note, choosing recovery mode from the grub boot menu allows the system to enter terminal mode

---

### Post by konradpiskorz on 2008-05-06
Hmm...

Well I reset my bios and that got rid of the following errors

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent.

However it still wont book :P

I was wondering where the boot logs are stored that would give me a clue as to where the failure is...

I'm looking at /var/log right now at the various logs.  Would /var/log/syslog be the file Im after?  It would be nice to see where boot is failing...

---

### Post by neurostu on 2008-05-06
Did you try booting the live CD to see if you can mount the partitions?, if you can then you should be able to copy your /home directory and any other files you need.

---

