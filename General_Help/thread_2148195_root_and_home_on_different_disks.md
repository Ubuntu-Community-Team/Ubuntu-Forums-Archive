---
title: "root and home on different disks"
date: 2013-05-24
forum: General Help
---

### Post by rasmus91 on 2013-05-24
Hello

I have an Asus UX32VD that has a 24 GB internal SSD and an 500 GB HD. I've install windows 7 on a 180 GB partition on the HD and then ubuntu 13.04 with the SSD working as the / mount location and the 320 GB working as the /home location.

I installed steam and then some of my games: Killingfloor, Half-life 2 death match, HL2: Episode 2 and L4D 2. And the system just warned me that theres almost no space left on the HD as i installed the last of the games, and I wonder about that. Steam has installed the games under the default path: /home/"username"/.local/share/Steam/SteamApps/common/"gamefolder"

shouldn't they be on the 320 GB drive rather than the SSD then?

if not, then how can i make it so?

Thank yo for your time.

---

### Post by Cheesemill on 2013-05-24
Can you post the output of....
```
df -h
sudo parted -l
```

---

### Post by rasmus91 on 2013-05-24
of course:

df -h
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb3        15G   14G  584K 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            4.9G   12K  4.9G   1% /dev
tmpfs           989M  888K  988M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            4.9G   19M  4.9G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda5       295G   54G  227G  20% /home

```

and:

sudo parted -l
```
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  106MB  105MB  primary   ntfs         boot
 2      106MB   178GB  178GB  primary   ntfs
 3      178GB   500GB  322GB  extended
 5      178GB   500GB  322GB  logical   ext4


Model: ATA SanDisk SSD i100 (scsi)
Disk /dev/sdb: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 2      1049kB  4296MB  4295MB  fat32           EFI system partition  hidden
 1      4296MB  8296MB  4000MB  linux-swap(v1)
 3      8296MB  24.0GB  15.7GB  ext4                                  boot



```

there you go :)

---

