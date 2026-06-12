---
title: "Corrupted ext4 filesystem after mdadm manipulation error"
date: 2014-04-23
forum: General Help
---

### Post by cronos6 on 2014-04-23
Hi,

   For the third time, I had to change a failed drive from my home linux RAID5 box. Previous one went right and this time, I don't know what I did wrong, but I broke my RAID5. Well, at least, he didn't want to start.
   /dev/sdb was the failed drive
   /dev/sdc and /dev/sdd are OK.

   I tried to reassemble the RAID with this command after I replace sdb and create a new partition :
   ```
~# mdadm -Cv /dev/md0 --assume-clean --level=5 --raid-devices=3 /dev/sdc1 /dev/sdd1 /dev/sdb1
```

   -> '-C' was not a good idea here  

   Well, I guess I did an another mistake here, I should have done this instead :
   ```
~# mdadm -Av /dev/md0 --assume-clean --level=5 --raid-devices=3 /dev/sdc1 /dev/sdd1 missing
```


   Maybe this wipe out my data...

   Let's go futher, then, pvdisplay, pvscan, vgdisplay returns empty
   information :-(

   Google helped me, and I did this :
   ```
~# dd if=/dev/md0 bs=512 count=255 skip=1 of=/tmp/md0.txt
```

```
	[..]
	physical_volumes {
		pv0 {
			id = "5DZit9-6o5V-a1vu-1D1q-fnc0-syEj-kVwAnW"
			device = "/dev/md0"
			status = ["ALLOCATABLE"]
			flags = []
			dev_size = 7814047360
			pe_start = 384
			pe_count = 953863
		}
	}
	logical_volumes {

		lvdata {
			id = "JiwAjc-qkvI-58Ru-RO8n-r63Z-ll3E-SJazO7"
			status = ["READ", "WRITE", "VISIBLE"]
			flags = []
			segment_count = 1
	[..]
```


   Since I saw lvm information, I guess I haven't lost all information yet...

   I tried an unhoped command :
   ```
~# pvcreate --uuid "5DZit9-6o5V-a1vu-1D1q-fnc0-syEj-kVwAnW" --restorefile /etc/lvm/archive/lvm-raid_00302.vg /dev/md0
```

   Then,
   ```
~# vgcfgrestore lvm-raid
```

   ```
~# lvs -a -o +devices
   LV     VG       Attr   LSize   Origin Snap%  Move Log Copy%  Convert  Devices
   lvdata lvm-raid -wi-a- 450,00g                                                     /dev/md0(148480)
   lvmp   lvm-raid -wi-a-  80,00g                                                     /dev/md0(263680)
```

   Then :
   ```
~# lvchange -ay /dev/lvm-raid/lv*
```

   I was quite happy until now.
   Problem appears now when I try to mount those 2 LV (lvdata & lvmp) as ext4 partition :
   ```
~# mount /home/foo/RAID_mp/
```

   ```
~# mount | grep -i mp
      /dev/mapper/lvm--raid-lvmp on /home/foo/RAID_mp type ext4 (rw)
```

```
   ~# df -h /home/foo/RAID_mp
      Filesystem                            Size  Used Avail Use%   Mounted on
      /dev/mapper/lvm--raid-lvmp   79G   61G   19G  77%   /home/foo/RAID_mp
```


   Here is the big problem
```
   ~# ls -la /home/foo/RAID_mp
      total 0
```

   I did a LVM R/W snapshot on the /dev/mapper/lvm--raid-lvmp LV, I fsck it. I recover 50% of the files only, all located in lost-+found/ directory with names heading with #xxxxx.

   I would like to know if there is a last chance to recover my data ?

   Thanks

---

### Post by cronos6 on 2014-04-24
Up please :-(

---

### Post by cronos6 on 2014-05-04
I'm guessing I did wrong when I've rebuilt my RAID, right ?

Please help :-(

---

