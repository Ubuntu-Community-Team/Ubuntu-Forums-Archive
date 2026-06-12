---
title: "btrfs balance benefits?"
date: 2013-07-12
forum: General Help
---

### Post by DrAlbert on 2013-07-12
Hi
I have a single partition and use it as root with btrfs filesystem. I know the use of balance command in raid partitions. but I don't know is there any benefit to use it in single partition or not?


```
user@----------:~$ sudo btrfs fi show
Label: 'Kubuntu'  uuid: fc8fd878-d9ad-472a-9503-5d45b35cf0b7
	Total devices 1 FS bytes used 28.07GB
	devid    1 size 93.22GB used 40.04GB path /dev/sda1
Btrfs v0.20-rc1


user@----------:~$ sudo btrfs fi df /
Data: total=34.01GB, used=26.02GB
System, DUP: total=8.00MB, used=12.00KB
System: total=4.00MB, used=0.00
Metadata, DUP: total=3.00GB, used=2.04GB
Metadata: total=8.00MB, used=0.00

```

---

