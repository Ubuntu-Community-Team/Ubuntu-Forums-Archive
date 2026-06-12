---
title: "Partition woes... removing xp"
date: 2008-04-19
forum: General Help
---

### Post by wildcoyote on 2008-04-19
I've been using Ubuntu for a while now - its got to be at least a year, I dual boot installed it and have never needed to use windows XP.

I've run out of space and decided to use gpartition to remove the windows install. I downloaded the ISO burnt it and booted up - only to find that it doesnt show a seperate partition for xp... just an entre partition which includes my linux install - so no way am I going to remove that.

When I go to  Places > My Computer - ubuntu shows me that I have a couple of media direct places, and entering them (having to enter password each time) I can see that they are in fact my windows partitions.

I need to delete these and reformat them so that ubuntu recognises them... but how?

I've been through lots of threads on here (several weeks of searching) but nothing definitive.

Any help appreciated.

Thanks in advance,

---

### Post by jameswillmer on 2008-04-19
post the results of 

> sudo fdisk -l

here

---

### Post by wildcoyote on 2008-04-19
Thanks for your help.

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        9077        9337     2096451    c  W95 FAT32 (LBA)
/dev/sda2              11        2644    21157605    7  HPFS/NTFS
/dev/sda3            2645        9337    53761522+   f  W95 Ext'd (LBA)
/dev/sda4            9338        9729     3148740   db  CP/M / CTOS / ...
/dev/sda5            9077        9337     2096451   dd  Unknown
/dev/sda6   *        2645        8811    49536364+  83  Linux
/dev/sda7            8812        9076     2128581   82  Linux swap / Solaris

Partition table entries are not in disk order


---

### Post by koenn on 2008-04-19
looks messy. I'd seriously consider starting from scratch if you have a disk or other media to backup your Ubuntu system.

This is what your disk probably looks like : 

```

Device 		Boot 	Start 	End 	Blocks 	Id 	System					
/dev/sda2 		11 	2644 	21157605 7 	HPFS/NTFS				Windows XP / NTFS data partition ?
/dev/sda3 		2645 	9337 	53761522+ f W95 Ext'd (LBA)			Extended partition containing 3 or 4 logical partitions
	/dev/sda6 * 	2645 	8811 	49536364+ 83 Linux					Linux /
	/dev/sda7 	8812 	9076 	2128581 82 	Linux swap / Solaris	Linux swap
	/dev/sda1 * 	9077 	9337 	2096451 c 	W95 FAT32 (LBA)			Bootable fat32 partition : windows c:\ ? old win98 partition ?
	/dev/sda5 	9077 	9337 	2096451 dd 	Unknown						completely overlaps with sda1. strange.
/dev/sda4 		9338 	9729 	3148740 db 	CP/M / CTOS / ...		??


```
what's weird is that you have sda5 completely overlapping sda1, and that sda1 is marked bootable ("active partition" in Windows speak, i.e. the partition that you'll boot Windows off) while it's a logical partition inside an extended partition. you'd expect this to be a primary partition like sda2 - but that one isn't marked "active".
sda4 might be some vendor-specific recovery partition.

you'll probably want to 
-delete sda5 and sda4, reboot see if everything still works
-delete sda1 and sda2, reboot, see if everything works
- run gparted (from a cd) to move / copy / ... the linux partitions  (+ reboot, see if everything is OK). 
- enlarge linux partitions or create additional new partitions


a backup of data you don't want to risk losing is definitely a good idea, because it really looks messy, and therefore rather unpredictable. You may have to set up swap anew and may need to re-install or update grub to get you linux system bootable again. 

no guarantees - try at your own risk.

---

### Post by wildcoyote on 2008-04-19
Thanks Koen,

I might take the easy option and do a complete wipe and reinstall.

---

