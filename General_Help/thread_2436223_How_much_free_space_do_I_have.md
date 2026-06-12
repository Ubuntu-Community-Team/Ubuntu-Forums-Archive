---
title: "How much free space do I have ?????"
date: 2020-02-02
forum: General Help
---

### Post by uwe-bungto on 2020-02-02
3 days ago I had about 300GB of data in my /home. I then used Bleachbit(as root) clean the free space. 12 or so hours later there is a warning 0 bits free :confused: I move one dirs with about 200GB to another hdd and ended up sith 62Gb free.](*,) 

Screen shot from natulis properties

[IMG]'/home/jpb/Pictures/Screen shots/Properties home dir.png'[/IMG]

Screen shot from gparted

[IMG]'/home/jpb/Pictures/Screen shots/Gparted home dir.png'[/IMG]

There even seems to be a 40Gb difference


Has this happened to anyone?

---

### Post by guiverc on 2020-02-02
One is showing GiB, the other GB.  They are not the same.

One picture also shows a folder, the other a partition (not the same thing)

---

### Post by uwe-bungto on 2020-02-02
/home is on its own HDD would the file browser and gparted not be looking at the same thing, or does gparted take into account the file system overhead?

Would it not be simpler if programmers used the same units to discribe the same object in the same disrto? :)

---

### Post by TheFu on 2020-02-02
> **uwe-bungto said:**
> /home is on its own HDD would the file browser and gparted not be looking at the same thing, or does gparted take into account the file system overhead?

Would it not be simpler if programmers used the same units to discribe the same object in the same disrto? :)

File systems sometimes lie.  These are usually the "advanced" file systems.
GUI programs always lie, IME.  A few commands to learn the truth.
```

df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -o name,size,type,fstype,mountpoint
```

Those will show the storage on LVs and partitions.

Unit differences are a pain.

---

### Post by Holger_Gehrke on 2020-02-03
The ext-family of filesystems reserve some space for use by root. This is primarily meant to ensure that the system keeps running (to some degree) even if a user manages to fill up the disk. You can use 'tune2fs -l /dev/sda1' (might need 'sudo' because it reads the superblock directly) to see the block size and the number of reserved blocks. The same program with other options can be used to set the percentage of reserved blocks, see the manual (man tune2fs) for details. On my system free space as reported by df and the reserved blocks add up to the number reported by gparted ...

Holger

---

### Post by TheFu on 2020-02-03
> **Holger_Gehrke said:**
> The ext-family of filesystems reserve some space for use by root. This is primarily meant to ensure that the system keeps running (to some degree) even if a user manages to fill up the disk. You can use 'tune2fs -l /dev/sda1' (might need 'sudo' because it reads the superblock directly) to see the block size and the number of reserved blocks. The same program with other options can be used to set the percentage of reserved blocks, see the manual (man tune2fs) for details. On my system free space as reported by df and the reserved blocks add up to the number reported by gparted ...

Holger

Typically, 5% is reserved in this way.  For /var and / , it is absolutely critical that the file system not become full.  But for data file systems, 5% wasted storage just isn't needed.  I usually **tune2fs** the setting for reserved blocks on data volumes.  On a 4TB volume, 5% is 200GB!  That's a huge amount of waste.
With the OS, I try to make the / partition 25G, so the reserved storage of 1.25G is just about perfect to prevent system lockups.  Thanks to **logwatch**, I get daily notification if the available storage drops too far.

---

### Post by uwe-bungto on 2020-02-03
After a little head scratching the issue was resolved. A crashed bleachbit, free space wipe, operation left enough write protected garbage in "/.local/share/Trash/expunged" to fill the disk. I think it is best to avoid that wipe function in the future.
Thanks
On to the next adventure :)

---

