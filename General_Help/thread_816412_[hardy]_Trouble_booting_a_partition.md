---
title: "[hardy] Trouble booting a partition"
date: 2008-06-02
forum: General Help
---

### Post by Oktotorf on 2008-06-02
Hello, as the title says I'm having trouble booting a certain partition.
This the output of sudo fdisk -l:
(sorry it's in dutch but I guess you'll understand what's important)

```

Schijf /dev/sda: 300.0 GB, 300090728448 bytes
255 koppen, 63 sectoren/spoor, 36483 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xffaddf2b

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1       36483   293049666    7  HPFS/NTFS

------------------------------------------------------

Schijf /dev/sdb: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x85a4154c

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           1       14946   120053713+   7  HPFS/NTFS

------------------------------------------------------------

Schijf /dev/sdc: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x6a40e0fc

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1   *           1        3434    27583573+   7  HPFS/NTFS
/dev/sdc2            3435        6091    21342352+  83  Linux
/dev/sdc3            6092        6340     2000092+  82  Linux wisselgeheugen
/dev/sdc4            6341       60801   437457982+  83  Linux

------------------------------------------------------------------------

Schijf /dev/sdh: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x12345678

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdh1   *           1       60801   488384001    c  W95 FAT32 (LBA)

```

So: 4 disks: two times NTFS, then 1 disk with 4 partitions, and then one external disk.

PROBLEM:
sda1 isn't mounted by itself and when I create a folder in media and try this:
**sudo mount /dev/sda1 /media/sda1**
it says:
**"mount: apparaat /dev/sda1 bestaat niet"** translated: **"mount: device /dev/sda1 doesn't exist"** So it shows up when I do fdisk -l but it's not in my /dev folder...
I also installed Gparted to see if this show something and here's what I get:
[img]http://img178.imageshack.us/img178/2677/schermafdrukwd7.png[/img]
The warning says: Unable to read the contents of this filesystem!

Then I installed Ntfsfix. When I do this:  **sudo ntfsfix /dev/sda ** 
I get this message:
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

So I went to Windows Xp (where the partition shows up like it's supposed to) and did a chkdsk /f and chkdsk /r on that partition, 2 times resulting in no errors. 

This leaves me out of ideas, which is why I'm posting my problem here...

---

