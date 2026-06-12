---
title: "Unallocated Partition Help"
date: 2008-04-27
forum: General Help
---

### Post by b3n87 on 2008-04-27
Hello, my friend has recently decided to try Ubuntu! He has an extra hard drive which has all his music on it. The problem is Windows did not format the hard drive at all, so in GNOME Partition Editor is calling it unallocated.

Is there a way we can mount it so we can copy all the music off it onto the Ubuntu desktop?

the hard drive (i think) its located at /dev/sdb, but its not there if you navigate through the file system to find it?

Kind regards

---

### Post by TeoBigusGeekus on 2008-04-27
How can an unformatted drive contain any kind of data?

---

### Post by b3n87 on 2008-04-27
I have no idea, according to the Partition Editor its "unallocated" but it does have Music and data on it.

Shall i post some command outputs for more information?

---

### Post by TeoBigusGeekus on 2008-04-27
Yes please!!!

---

### Post by b3n87 on 2008-04-27
what commands shall i use?

---

### Post by b3n87 on 2008-04-27
Disk /dev/sda: 163.9 GB, 163928604672 bytes
161 heads, 15 sectors/track, 132576 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      111154   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
161 heads, 15 sectors/track, 111153 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      111154   134217727+   4  FAT16 <32M

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25352534

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux

---

### Post by nibsa1242 on 2008-04-27
I was trying to help him in IRC chat. At that time I had him pastebin a sudo fdisk -l the results follow or you can see [http://paste.ubuntu-nl.org/64767/](http://paste.ubuntu-nl.org/64767/).

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25352534

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
161 heads, 15 sectors/track, 132576 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      111154   134217727+   4  FAT16 <32M

Disk /dev/sdb1: 137.4 GB, 137438952960 bytes
161 heads, 15 sectors/track, 111153 cylinders
Units = cylinders of 2415 * 512 = 1236480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           1      111154   134217727+   4  FAT16 <32M



According to [http://www-personal.umich.edu/~hnarayan/maxtor-harddrive-linux.html](http://www-personal.umich.edu/~hnarayan/maxtor-harddrive-linux.html) if one has a partition named /dev/sdxp1 that partition does not have a node. This is sometimes done by drive manufacturers / computer OEMs. I can not seem to find a single instance of anyone who had a drive like this that Linux was happy reading.

The best way to get the data off of the disk is probably to take the second hard disk with the media files on it, and connect it to a computer running Windows. Hopefully, the Windows computer will be able to read the drive. Then the files can be copied off. Once the files are backed up, you should use Linux to format the drive so Linux can understand it.

---

### Post by TeoBigusGeekus on 2008-04-27
What drives do you see when you go to /media?

---

### Post by b3n87 on 2008-04-28
Hi guys, thanks for your help.
in the folder "media" he has the following folders

cdrom cdrom0 floppy floppy0


none of which is the second hard drive :/

Im not sure why, but windows has allowed him to use the drive unformatted. hmmmm

---

### Post by b3n87 on 2008-04-28
hello again, i think he's gonna buy this

[SATA 2 USB Cable]("http://cgi.ebay.co.uk/USB-2-0-TO-SATA-IDE-CABLE-FOR-HDD-W-POWER-ADAPTER-UK_W0QQitemZ350052764288QQihZ022QQcategoryZ74941QQssPageNameZWDVWQQrdZ1QQcmdZViewItem")

Copy the files to a vista laptop, format the hard drive then copy the files back for Ubuntu to read. Does ubuntu have a problem with the way Vista formats a hard-drive, new version of NTFS or anything silly like that? Or I could use the Ubuntu live CD with the GNOME Partition Editor?

---

### Post by TeoBigusGeekus on 2008-04-28
No, Ubuntu has no problem with that...
But your problem still seems to me really weird...
Unless there's something we're missing, that's the proper way to continue...

---

### Post by nibsa1242 on 2008-04-28
That sounds like it will do what you want it to do. Ubuntu shouldn't have a problem with the way Windows formats the drive, but just to be safe I would use the GNOME Partition Editor to at least remove the partitions that you see on the drive. You just want to make sure that the strange sdxp1 partition does not exist anymore, as every case that I can find of a sdxp1 partition results in inablity of Linux to be able to read / understand the file system. 

I think you might be able to delete the partitions in Windows from a command prompt with fdisk, if it even exists in Vista.

---

### Post by om1 on 2008-04-29
hmmm... thinks for the post.... ive never ran into that issue before... that was very informative :popcorn:

---

### Post by b3n87 on 2008-04-29
its completely bizare! but its definatly not formated in a way that you would expect it to be. Ill keep you lot posted when i get it all sorted. if I manage to do that.....

---

### Post by b3n87 on 2008-04-30
just a thought, its a SATA drive, they are ment to be formatted in FAT32 arent they?

---

