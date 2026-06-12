---
title: "Mounting fakeRAID on Startup?"
date: 2007-11-12
forum: General Help
---

### Post by Nexusx6 on 2007-11-12
Hello :) I need a little help in figuring out how to mount a fakeRAID with NTFS at startup in Ubuntu. Currently I use *sudo mount -t ntfs-3g /dev/mapper/nvidia_fidfcidf1 /media/windows/* to mount through terminal, but I have no idea what I need to put into fstab to do this at start up.

If it helps:
> fox@aurora-project:~$ sudo dmraid -ay
RAID set "nvidia_fidfcidf" already active
RAID set "nvidia_fidfcidf1" already active
fox@aurora-project:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_fidfcidf", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_fidfcidf", stripe, ok, 488397166 sectors, data@ 0 

Thanks for any help

---

### Post by fjgaude on 2007-11-12
Try adding this as the last line to /etc/fstab:

```
/dev/mapper/nvidia_fidfcidf /media/windows ntfs-3g defaults 0 0
```

That should work. Let us know.

---

### Post by Nexusx6 on 2007-11-14
> **fjgaude said:**
> Try adding this as the last line to /etc/fstab:

```
/dev/mapper/nvidia_fidfcidf /media/windows ntfs-3g defaults 0 0
```

That should work. Let us know.

Sorry it took me so long to respond, haven't been at my computer the past few, but unfortunatly that string hasn't gotten Ubuntu to mount the raid array

---

### Post by fjgaude on 2007-11-14
I guess you get no error message, eh?

I don't know what to suggest... maybe try just ntfs and not the ntfs-3g. You do have ntfs-3g installled? It's in the Gutsy distro. Such recognizes ntfs automatically.

Let us know how you make out.

---

### Post by Nexusx6 on 2007-11-14
Got it to work :D

I took a hint from the command line input that I was using to mount it and put the number 1 at the end of */dev/mapper/nvidia_fidfcidf* -- low and behold, it mounted. Though I'm not sure why I had to make it /dev/mapper/nvidia_fidfcidf1 to get it to work /shrug

Thanks for the help mate (^^)b

---

### Post by fjgaude on 2007-11-14
Amazing... we learn something new every day.

---

### Post by gimmic on 2007-11-15
I've got almost an identical setup here. I've got all my backups / files on an NTFS nvraid.

I can get the raid mounted, but get io errors:

```
gimmic@waveboxen:/dev$ sudo dmraid -ay
RAID set "nvidia_fgchbaig" already active
RAID set "nvidia_fgchbaig1" already active
gimmic@waveboxen:/dev$ sudo dmraid -r
/dev/sdc: nvidia, "nvidia_fgchbaig", stripe, ok, 976773166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_fgchbaig", stripe, ok, 976773166 sectors, data@ 0
gimmic@waveboxen:/dev$ mount|grep fgc
/dev/mapper/nvidia_fgchbaig1 on /media/raid type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
gimmic@waveboxen:/dev$ sudo ls /media/raid
ls: /media/raid: Input/output error

```

Any suggestions?

---

### Post by fjgaude on 2007-11-15
What happens if you change the fuseblk to ntfs or ntfs-3g?

Are you sure the array is mounted?

Try using sudo fdisk -l.

---

### Post by gimmic on 2007-11-15
When I mount with ntfs-3g OR ntfs, it appears to show up as fuseblk. I get the same input/output error when accessing it using either.

```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bfd0bfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0db7928d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bd75a56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976768033+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/dm-0: 1000.2 GB, 1000215674880 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bd75a56

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      121602   976768033+   7  HPFS/NTFS

Disk /dev/dm-1: 1000.2 GB, 1000210466304 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

```

gimmic@waveboxen:/dev/mapper$ /bin/ntfs-3g /dev/raid-bravo /media/raid -o debug
Version 1.913
Mounted /dev/raid-bravo (Read-Write, label "RAID0", NTFS 3.1)
Cmdline options: debug
Mount options: noatime,silent,allow_other,nonempty,fsname=/dev/raid-bravo,blkdev,blksize=4096,user=gimmic
unique: 1, opcode: INIT (26), nodeid: 0, insize: 56
INIT: 7.8
flags=0x00000003
max_readahead=0x00020000
   INIT: 7.8
   flags=0x00000001
   max_readahead=0x00020000
   max_write=0x00020000
   unique: 1, error: 0 (Success), outsize: 40
gimmic@waveboxen:/dev/mapper$ unique: 2, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 2, error: 0 (Success), outsize: 112

```


```

gimmic@waveboxen:~$ sudo mount -t ntfs-3g /dev/mapper/nvidia_fgchbaig1 /media/raid
gimmic@waveboxen:~$ mount|grep /raid
/dev/mapper/nvidia_fgchbaig1 on /media/raid type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
..
gimmic@waveboxen:~$ sudo mount -t ntfs /dev/mapper/nvidia_fgchbaig1 /media/raid
gimmic@waveboxen:~$ mount|grep /raid
/dev/mapper/nvidia_fgchbaig1 on /media/raid type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
gimmic@waveboxen:~$ sudo ls /media/raid 
ls: /media/raid: Input/output error

```

---

### Post by fjgaude on 2007-11-15
I don't have any thoughts on what could be wrong, except these are some big drives! I wonder if there is a problem with ntfs handling them? I've never used such before, we're in a new era.

dmraid is something I don't use, only tested sometime back to see how fast it was compared to mdadm. I saw that I needed better controllers, ones not on the PCI bus, to get high throughput, over the 133 MB/sec limit of PCI, and thus PCI-Express, or the old PCI-X.

Maybe someone else here has an idea as to what to try next.

---

### Post by gimmic on 2007-11-15
Sigh, I was not expecting this with the array.
I guess it's kind of a show stopper if I can't get the thing mounted rw. no matter how i mount it, it mounts using fuse.

---

