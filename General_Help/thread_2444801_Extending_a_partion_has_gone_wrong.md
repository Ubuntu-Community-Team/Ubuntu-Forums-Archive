---
title: "Extending a partion has gone wrong"
date: 2020-06-04
forum: General Help
---

### Post by gck303 on 2020-06-04
[COLOR=#000000]I have just attempted to extend a partion and got into a mess. I had already trialled it on a seperate disk, but now working on a larger file system it has gone wrong.[/COLOR]

[COLOR=#000000]FWIW I am using Ubuntu server installed on a HPE server with a 4TB hardware raid plit into a group of small logical disks. The HPE part is working fine.[/COLOR]

[COLOR=#000000]The original partition table from fdisk is below.

```
[/COLOR][COLOR=#000000][FONT=&quot]Disk /dev/sdc: 732.4 GiB, 786432000000 bytes, 1536000000 sectorsUnits: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 262144 bytes / 1310720 bytes
Disklabel type: dos
Disk identifier: 0x0cd9c822


Device     Boot Start        End    Sectors  Size Id Type [COLOR=#000000][FONT=&quot]/dev/sdc1        2048 1228799999 1228797952  586G 83 Linux[/FONT][/COLOR][COLOR=#000000]
```

[/COLOR][COLOR=#000000]I deleted this parting and exited fdisk. Then when I tried to create a new partition the starting block has changed from 2048 to 2560!!!! I did try to set it to 2048, but it said 'Value out of range.'.[/COLOR]

[COLOR=#000000]This new partition table has been saved. But... I am concerned that the start of the partition is different.[/COLOR]

[COLOR=#000000]What do I do next?[/COLOR]

[COLOR=#000000]I am aware that I can easily loose all my data. And I do not want to do this. (It is only somewhat less important data, so has not been fully backed up. I didn't really want to transfer the 700GB to backblaze...)

```
[/COLOR][COLOR=#000000][FONT=&quot]Command (m for help): pDisk /dev/sdc: 732.4 GiB, 786432000000 bytes, 1536000000 sectors[/FONT][/COLOR]
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 262144 bytes / 1310720 bytes
Disklabel type: dos
Disk identifier: 0x0cd9c822


Device     Boot Start        End    Sectors   Size Id Type [COLOR=#000000][FONT=&quot]/dev/sdc1        2560 1535999999 1535997440 732.4G 83 Linux[/FONT][/COLOR][COLOR=#000000]
```
[/COLOR]

---

### Post by kneutron on 2020-06-04
--Let me get this straight, you took an active disk that had not been backed up, and deleted the partition table out from under it??  Why would you not use **gparted**, or even parted?  What were you trying to accomplish?

See:
[http://sirlagz.net/2016/01/20/live-resizing-lvm-on-linux/](http://sirlagz.net/2016/01/20/live-resizing-lvm-on-linux/)

---

### Post by gck303 on 2020-06-04
Did you have a positive suggestion to make?

---

### Post by kneutron on 2020-06-05
--Yeah. I posted a link.  Did you bother reading it?  That article shows you how to extend a partition without kicking its feet out from under it.  Maybe refer to it (or, you know, *as I mentioned*, use **gparted**) next time -after- backing up your data.

--Keep in mind you're asking for free help on a volunteer forum.   Most of us have suffered data loss and have learned there are safer/better ways to do things.  Also, we try to learn from others, and try not to make the same mistake twice.

--If you want to try and recover anything from that drive as it is now, you can try photorec or testdisk.  But it's no guarantees, and it will be a slog.

[https://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](https://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

