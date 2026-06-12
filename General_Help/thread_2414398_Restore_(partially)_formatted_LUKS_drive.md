---
title: "Restore (partially?) formatted LUKS drive"
date: 2019-03-09
forum: General Help
---

### Post by schmidtdominik on 2019-03-09
I just accidentally formatted my 2TB hard drive and may have lost all my files 


On this hard drive were:

- ~1.7TB encrypted LVM-LUKS Container
- ~250GB Partition NTFS




I don't care about the data in the unencrypted NTFS partition but the other one is **really really** important to me.


I used the Gnome "Disks" utility and formatted it with the options "GPT partition table" and "overwrite existing data" (complete wipe). I noticed that I selected the wrong disk just a few seconds after starting it and immediately unplugged it.

Testdisk produced the following output:

```
The following partition can't be recovered:
     MS Data               3906963422 4395241404  488277983
     NTFS, blocksize=4096, 249 GB / 232 GiB


Results
     MS Data                     2046 3906963413 3906961368
     ext4 blocksize=4096 Large_file Sparse_SB Backup_SB, 2000 GB / 1862 GiB
     MS Data                     2048       6143       4096
     LUKS 1 (Data size unknown), 2097 KB / 2048 KiB
     MS Data               3418685440 3906963422  488277983
     NTFS found using backup sector, blocksize=4096, 249 GB / 232 GiB


Hint for advanced users. dmsetup may be used if you prefer to avoid to rewrite the partition table for the moment:
echo "0 3906961368 linear /dev/sda 2046" | dmsetup create test0
echo "0 4096 linear /dev/sda 2048" | dmsetup create test1
echo "0 488277983 linear /dev/sda 3418685440" | dmsetup create test2


interface_write()
 
No partition found or selected for recovery
```

Apparently there still exists a LUKS header. [This thread]("https://www.linuxquestions.org/questions/linux-general-1/recovering-formatted-luks-ext4-partition-4175537666/") says that I should create a new partition starting from the start of the LUKS partition but I'm not sure where that is and how I should do this?

---

### Post by HermanAB on 2019-03-09
LUKS?  You should go and dig in your backups.

---

