---
title: "HDD Formatting Trouble"
date: 2007-06-14
forum: General Help
---

### Post by domat00 on 2007-06-14
Hi, this is my first post in this particular category, so I'll get right to the point:

I've got a 150GB Raptor that I use for my OS, and a 250GB Caviar that I use for storage.  I recently migrated from Windows and I'm ready to get rid of it, but to do so I need to stick a file onto the Caviar, and that's where I come up empty.  I can't format the stinkin' drive!  Now, to be completely convenient, GParted should work, but when I tried to create a partition I always came up with a drive that I had insufficient privileges to *view*.  So that's out of the window.  You guys got another program not in the repos I could use to format that drive (whole drive, I can create sub-folders later) in ext3, or *gasp* NTFS with the right permissions?

Also, for GParted, I get this error when I try and create a new primary partition in ext3 using the whole disc:  Cannot mount volume: wrong fs type etc., (dialog goes away before I can even write the rest down...)

And also, I'm getting tired of not apparently being the owner or root.  This is part of my problem; I don't have rights to some things when I should have rights to everything!!  I installed Ubuntu on this computer, and I set up a single account (me), and I'm not known as root, I can't change permissions on anything except for what I create, and apparently there's another owner that I don't know about.  Perhaps I'm just not ready for Linux.

Thanks in advance.

---

### Post by smoker on 2007-06-14
i always use the 'gparted live-cd' for any partitioning and never had any problems with it:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by domat00 on 2007-06-14
Well, I tried using that, but I looked at an error GParted saved as root when i gksudo'd nautilus, and here is what it reads:

GParted 0.2.5

Create Primary Partition #1 (ext3, 232.88 GiB) on /dev/sda    ( ERROR )
     	
create empty partition    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 488392064
size: 232.88 GiB
set partitiontype    ( SUCCES )
create new ext3 filesystem    ( ERROR )
     	
mkfs.ext3 /dev/sda1
     	
mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted; will not make a filesystem here!

========================================

Here's the fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9120    73256368+   7  HPFS/NTFS
/dev/sdb2            9121       17992    71264340   83  Linux
/dev/sdb3           17993       18241     2000092+  82  Linux swap / Solaris

and a df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb2             70145564  41433300  25149048  63% /
varrun                  517864        96    517768   1% /var/run
varlock                 517864         0    517864   0% /var/lock
procbususb              517864       120    517744   1% /proc/bus/usb
udev                    517864       120    517744   1% /dev
devshm                  517864         0    517864   0% /dev/shm
lrm                     517864     33788    484076   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             73256364  42476688  30779676  58% /media/sdb1
/dev/hdc                 49750     49750         0 100% /media/cdrom0
/dev/sda1            244196000     73440 244122560   1% /media/disk

Hope that's enough info for somebody to give me a hand.  :p

---

