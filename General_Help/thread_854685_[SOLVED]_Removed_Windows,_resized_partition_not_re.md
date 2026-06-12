---
title: "[SOLVED] Removed Windows, resized partition not recognizing new disk space"
date: 2008-07-09
forum: General Help
---

### Post by mkendall on 2008-07-09
I used gparted to remove my Windows partition and resize my 2nd partition to take up the freed space. An error occured while checking (and possibly fixing) the new partition for errors. Now my system doesn't recognize the freed space.

Here's the results of **fdisk -l**
```
Disk /dev/sda: 100.0 GB 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot	Start	End	Blocks		Id	System
/dev/sda2	1	5332	42829258+	83	Linux
/dev/sda3	5333	11950	53159085	83	Linux
/dev/sda4	11951	12135	1486012+	5	Extended
/dev/sda5	11951	12135	1485981		82	Linux swap / Solaris
```

and this is my **fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d441f730-19ee-469e-ac73-68ff17ddc072 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=002019bb-0001-4bd8-9a4e-a7bb19688802 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1	/media/Win	ntfs-3g	defaults	0	0
/dev/sda2	/media/Part2	ext3	defaults	0	0
```

Fortunately, no data has been lost, but I could really use that extra 24 gb.

Also, how do you copy from the terminal? I know shift+insert copies to the terminal, but how do you go the other way?

Thanks

---

### Post by plucky on 2008-07-09
Can you post output of ```
df -h
```

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d441f730-19ee-469e-ac73-68ff17ddc072 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=002019bb-0001-4bd8-9a4e-a7bb19688802 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
[color=red]/dev/sda1	/media/Win	ntfs-3g	defaults	0	0[/color]
/dev/sda2	/media/Part2	ext3	defaults	0	0

As /dev/sda1 doesn't exist anymore,you should remove the highlighted line from fstab.Your sda2 partition is seen as 42.8G by fdisk.
> Now my system doesn't recognize the freed space.

Where are you seeing this?

---

### Post by mkendall on 2008-07-09
> **plucky said:**
> Can you post output of ```
df -h
```

```
Filesystem	Size	Used	Avail	Use%	Mounted on
/dev/sda3	50G	43G	5.0G	90%	/
varrun		248M	96K	248M	1%	/var/run
varlock		248M	0	248M	0%	/var/lock
udev		248M	68K	248M	1%	/dev
devshm		248M	0	248M	0%	/dev/shm
lrm		248M	34K	214M	14%	/lib/modules/2.6.22-15-generic/volatile
/dev/sda2	17G	9.4G	6.0G	62%	/media/Part2
```


> As /dev/sda1 doesn't exist anymore,you should remove the highlighted line from fstab.Your sda2 partition is seen as 42.8G by fdisk.
Done.

> Where are you seeing this?

See attachment.

---

### Post by plucky on 2008-07-10
> /dev/sda2	17G	9.4G	6.0G	62%	/media/Part2

Definitely not the right size.

Run gparted **System > Administration > Partition Editor** and select the sda2 partition and **unmount** it.Then select **check** to run and repair the file system.Then remount it ```
sudo mount -a
``` and see what it says.


Good Luck

---

### Post by mkendall on 2008-07-10
> **plucky said:**
> Definitely not the right size.

Run gparted **System > Administration > Partition Editor** and select the sda2 partition and **unmount** it.Then select **check** to run and repair the file system.Then remount it ```
sudo mount -a
``` and see what it says.


Good Luck

That did it. Thanks.

---

