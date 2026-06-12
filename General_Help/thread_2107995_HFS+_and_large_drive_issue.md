---
title: "HFS+ and large drive issue"
date: 2013-01-23
forum: General Help
---

### Post by DeathWolf on 2013-01-23
Hi all,

Running precise I am experiencing a problem mounting my 3TB HFS+ formatted drive.

Regardless of my attempts it errors with:
[681648.160023] hfs: invalid secondary volume header
[681648.160026] hfs: unable to find HFS+ superblock


Here's the drive info:
$ sudo parted /dev/sdb unit B print
Model: ATA WDC WD30EZRX-00D (scsi)
Disk /dev/sdb: 3000592982016B
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End             Size            File system  Name                  Flags
 1      20480B      209735679B      209715200B      fat32        EFI System Partition  boot
 2      209735680B  3000458743807B  3000249008128B  hfs+         
3TB-Backup


Things I've tried:
Direct mount:
sudo mount -t hfsplus /dev/sdb2 /testmnt

Offset mount:
sudo mount -t hfsplus -o ro,loop,offset=209735680 /dev/sdb /testmnt

Manual loop device offset mount:
sudo losetup -f /dev/sdb --offset 209735680 --sizelimit 3000249008128 --show
sudo mount -t hfsplus -o loop,force,ro /dev/loop0 /testmnt

Manual loop device direct mount:
sudo losetup /dev/sdb2 --offset 0 --sizelimit 3000249008128 --show
sudo mount -t hfsplus -o loop,force,ro /dev/loop0 /testmnt


None of this works.
For what it's worth, the block headers are per HFS+ specification in the right place:

$ sudo dd if=/dev/sdb2 bs=1024 skip=1 count=1|hd|head
00000000  48 2b 00 04 80 00 21 00  48 46 53 4a 00 00 15 d6  |H+....!.HFSJ....|
00000010  cd 0e 7c 22 cd 0f 0d 10  00 00 00 00 cd 0e 6e 12  |..|"..........n.|

$ sudo dd if=/dev/sdb2 bs=1024 skip=$((3000249008128/1024-1)) count=1|hd|head
00000000  48 2b 00 04 80 00 21 00  31 30 2e 30 00 00 15 d6  |H+....!.10.0....|
00000010  cd 0e 7c 22 cd 0e 6e 12  00 00 00 00 cd 0e 6e 12  |..|"..n.......n.|


Any ideas?

Thanks,

-fcpk/Paul-Kenji

---

### Post by tgalati4 on 2013-01-23
If not already, put the drive in a USB enclosure and find a Mac computer and use the Disk Utilities to verify and format the drive.  I don't trust the linux hfs+ utilities--or at least I have had issues with them.  After formatting on a Mac, the drive should mount OK.

A work-around is to partition the drive into smaller chunks and try to format each partition and mount it.

---

### Post by DeathWolf on 2013-01-23
So, the drive was formatted on a mac and used for a long time on a mac.
it currently contains important data, so I'd rather not touch in any non-ro ways:)

---

### Post by tgalati4 on 2013-01-23
It might be a bug with hfs+ in linux.  Have you searched for such a bug?  Do you have hfsutils installed?  Are there any tools in that package that could help mount the drive?

Was the drive used with Firewire on the Mac and now you are using USB to hook to the linux PC?

It could be a USB performance issue.

---

### Post by DeathWolf on 2013-01-23
hfsutil is installed.

I did search for bugs but found nothing

The drive was connected in sata on the mac and is on sata on the pc too

---

### Post by tgalati4 on 2013-01-23
Sounds like you have researched this issue.  Try filing a bug against hfsplus or hfsutils and follow it.  There might be a 2TB limitation or something else is going on.

---

