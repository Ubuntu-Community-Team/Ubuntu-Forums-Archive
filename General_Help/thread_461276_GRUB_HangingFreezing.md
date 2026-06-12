---
title: "GRUB Hanging/Freezing"
date: 2007-06-01
forum: General Help
---

### Post by Rob_Quads on 2007-06-01
I have hit a strange grub problem. Upon booting all the bios checks go through. I see the following then the system just hangs and i get no further.

```

GRUB Loading stage 1.5.

GRUB loading, please wait...

```

Some background - I have just changed motherboards and added a couple I/O cards so I am guessing it might be something to do with the way its changed the drive letters, the number of drives has stayed the same.

IF I disconnect one of the 4 drives in the RAID array the system boots as normal and runs fine but with all 4 connected it hangs

Previous Setup

```

Mothboard onboard IDE	Primary Master   =  80GB	/dev/hda
			Secondary Master = 120GB	/dev/hdc
IDE PCI Card		Primary Master   = 300GB	/dev/hdf	/md0 RAID5 array
			Primary Slave 	 = 300GB	/dev/hdg	/md0 RAID5 array
			Secondary Master = 300GB	/dev/hdh	/md0 RAID5 array
			Secondary Slave  = 300GB	/dev/hdi	/md0 RAID5 array
SATA PCI Card		1st 		 = 250GB	/dev/sda
			2nd		 = 250GB	/dev/sdb

```

After the change for some reason it really screwed up the ordering of the disks

```

Mothboard onboard IDE	Primary Master   =  80GB	/dev/hdi
			Secondary Master = 120GB	/dev/hdk
IDE PCI Card		Primary Master   = 300GB	/dev/hda	/md0 RAID5 array
			Secondary Master = 300GB	/dev/hdc	/md0 RAID5 array
IDE PCI Card		Primary Master   = 300GB	/dev/hde	/md0 RAID5 array
			Secondary Master = 300GB	/dev/hdg	/md0 RAID5 array
SATA PCI Card		1st 		 = 250GB	/dev/sda
			2nd		 = 250GB	/dev/sdb


```

Any ideas what could be causing this?

---

### Post by Rob_Quads on 2007-06-01
Hmm got a bit further. If I switched the ATA discs so that they were Master & Slave only using one PCI card (but leaving the other one there) then it boots fine. It just seems to hang when the discs are spread across the second IDE controller.

Bit of an **** as I want to give each disk a channel to increase performance.

---

### Post by BLTicklemonster on 2007-06-26
What are the chances you have a non boot disk in your cd tray, and your system is set to boot from cdrom first?

I have been seeing this problem; it just took me forever to boot, and dog goned if there wasn't a disk in the cd tray. Of course, I'm hesitant to boot again, because I don't want to wait if that wasn't the problem, you know.

But I will eventually have to boot, so at that point, I'll get back and let you know if that was my problem or not.

---

