---
title: "USB Drive Not Mounting- Startup Disk Creator"
date: 2013-11-01
forum: General Help
---

### Post by 7Starphy on 2013-11-01
I tried to create a Live USB using Startup Disk Creator . In that process I clicked the "Erase Disk" button (thinking it will format my USB Drive ) and my USB Drive does not seem to be working anymore. On trying
```
sudo parted -l
```

The output was 

```
Model: SanDisk Cruzer (scsi)Disk /dev/sdb: 4022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags




Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label     
```

Can someone help me with this ?

---

### Post by fantab on 2013-11-01
Install Gparted:
```
sudo apt-get update
sudo apt-get install gparted
```

Open Gparted. Select your USB Sandisk. In the gparted menu, go to 'Device' and 'create a new Partition Table'... Apply changes. Then recreate a partition.

---

### Post by 7Starphy on 2013-11-03
Ok I recreated the partition and applied the changes using GParted. Now my Pendrive is getting detected (which is good),but i am not able to send files to it (which is bad). Am I missing out anything ?

---

### Post by fantab on 2013-11-03
It should work. Try again. If not, then use [Unetbootin]("http://unetbootin.sourceforge.net/").

---

