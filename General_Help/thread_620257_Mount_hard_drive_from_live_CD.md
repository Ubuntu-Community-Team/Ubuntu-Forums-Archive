---
title: "Mount hard drive from live CD?"
date: 2007-11-22
forum: General Help
---

### Post by cwj88 on 2007-11-22
Is it possible to mount my windows hd as a non read only drive from the live CD?

I have a bunch of data on my external drive that I would like to move onto my windows drive, but my external drive isn't being recognized by windows.

The live CD is recognizing the drive.

---

### Post by cwj88 on 2007-11-22
anyone?

---

### Post by bodhi.zazen on 2007-11-22
What is the output of 

```
sudo fdisk -l
```???

---

### Post by cwj88 on 2007-11-22
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         498     3991552   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         498        9730    74157056    7  HPFS/NTFS

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2388    19181578+  83  Linux
/dev/sdb2            2389        2498      883575    5  Extended
/dev/sdb5            2389        2498      883543+  82  Linux swap / Solaris

```

---

### Post by geirha on 2007-11-22
On the liveCD, open a nautilus windows (the file browser). In the left margin you should see all the partitions on the harddrives listed as icons with the size next to them. Double click one to mount it, and it will change name to disk or disk-1 or something. Double click it again to browse its content.

---

### Post by cwj88 on 2007-11-22
I was using the kubuntu live cd

I tried it with the ubuntu live cd, it still did not work.  I went into places>computer and I saw the icon for the drive, and I tried to mount it.  It gave me an error saying that it could not mount the drive because it was not removable or something like that.

Do you think it would be easier if I installed ubuntu and dual booted and then moved the files from my external onto my windows partition?

---

### Post by geirha on 2007-11-23
Then I guess you'll have to do it manually. When the liveCD is up and running, open a terminal. Then 
```
sudo mkdir /media/sda2
sudo mkdir /media/sdb1

sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sdb1 /media/sdb1

```

---

### Post by cwj88 on 2007-11-23
yea I tried that but it tells me that the drive is read only when I try to do anything with it

---

### Post by geirha on 2007-11-23
What ubuntu release is the CD?

---

### Post by Sef on 2007-11-23
Get [Knoppix]("http://knoppix.com").  I have mounted hard drives with that live cd.

---

### Post by cwj88 on 2007-11-23
Knoppix worked, thanks!

---

