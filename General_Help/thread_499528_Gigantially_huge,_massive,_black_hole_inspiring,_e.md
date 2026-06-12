---
title: "Gigantially huge, massive, black hole inspiring, eat all McDonalds partition table pr"
date: 2007-07-12
forum: General Help
---

### Post by malfist on 2007-07-12
I have a major problem with my partition table, it doesn't work. I was having problems with it since I installed ubuntu. Partition Magic wouldn't work, ntfsresize wouldn't work, fdisk f'd it up, testdisk wanted to delete the windows partition, testdisk said it was a bad boot sector, testdisk rebuild boot sector, testdisk said it was a bad boot sector, cfdisk wouldn't work, GParted couldn't identify the ntfs partitions file system, etc.

I finally let Gpart have a go at it and let it repair the partition table. Now nothing works. I made a physical copy of the partition table though (w00t). Grub exits with error code 17 (handly that, tells me a lot). Damn Small Linux can mount and see the partitions without a problem, though the fdisk partition table doesn't look right.

This is the backup log fdisk made before my first edit:```

[FONT="Courier New"]#1183951184	Disk /dev/hdc - 200GB/186GiB	CHS 24321 255 63
#	start		size		id
-------------------------------------
1	63		147299922		7	*
3	171317160		51648975		83	P
2	222966135		167750730		0F	E
6	222966261		2329299		82	L
5	225295623		165421242		07	L[/FONT]
```

I don't have everything backed up like I should (its a 200GB hd and nearly full!), how can I fix this?
Does anyone have the faintest idea?
Anything?
Please?

---

### Post by malfist on 2007-07-13
Nevermind, formatted harddrive and installed Slackware.

---

