---
title: "Disk-space"
date: 2006-11-21
forum: General Help
---

### Post by zugu on 2006-11-21
Every time I boot up mu Dapper, it says that the / partition is 98% full. However, when I use Baobab or the disks-admin application, it says that I have 1.5 GB free on the partition. The apt-cache is clean, I store all my files on other partitions and I have a swap partition. The / partition is 4 GB.

Need help.

---

### Post by dcstar on 2006-11-22
> **zugu said:**
> Every time I boot up mu Dapper, it says that the / partition is 98% full. However, when I use Baobab or the disks-admin application, it says that I have 1.5 GB free on the partition. The apt-cache is clean, I store all my files on other partitions and I have a swap partition. The / partition is 4 GB.

Need help.

Open a terminal and do:
```
df -h
```

---

