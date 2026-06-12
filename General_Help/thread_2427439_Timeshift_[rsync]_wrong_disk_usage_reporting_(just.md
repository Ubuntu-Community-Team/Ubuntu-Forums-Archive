---
title: "Timeshift [rsync]: wrong disk usage reporting (just for information)"
date: 2019-09-22
forum: General Help
---

### Post by GhX6GZMB on 2019-09-22
I'm a happy Timeshift user, but have had problems with disk usage reporting from the Timeshift directories, both when using the File Manager as well as when listing the backup files from the Terminal.
Both list the Timeshift backup file sizes as being full backups in the GB range, which shouldn't happen, as Timeshift is supposed to do incremental backups. My disk usage is at this point ~13.1 GB.

I've now done a test with deleting a Timeshift backup and creating a new one:

```

macro@macro-pc:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           388M  1,4M  386M   1% /run
/dev/sda1       220G   26G  183G  13% /
tmpfs           1,9G   71M  1,9G   4% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
tmpfs           388M  8,0K  388M   1% /run/user/1000
/dev/sdb1        29G   14G   14G  51% /media/macro/fb2afce9-d346-4b81-bfe6-c3cf5cb6f217

macro@macro-pc:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           388M  1,4M  386M   1% /run
/dev/sda1       220G   26G  183G  13% /
tmpfs           1,9G  8,1M  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
tmpfs           388M  8,0K  388M   1% /run/user/1000
/dev/sdb1        29G   13G   15G  46% /media/macro/fb2afce9-d346-4b81-bfe6-c3cf5cb6f217

macro@macro-pc:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           388M  1,4M  386M   1% /run
/dev/sda1       220G   26G  183G  13% /
tmpfs           1,9G  8,1M  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
tmpfs           388M  8,0K  388M   1% /run/user/1000
/dev/sdb1        29G   14G   14G  52% /media/macro/fb2afce9-d346-4b81-bfe6-c3cf5cb6f217


```

The first part is the original Timeshift file size on sdb1 containing two backups.
The second is the file on sdb1 with one backup deleted.
The third is the file on sdb1 with an even larger backup added (/root and /home included).

From the disk usage, Timeshift is truly incremental, but in the file size listing it's somehow not.
I've no idea why, these are just my findings.
Perhaps someone has an idea?


Cheers.

---

### Post by Skaperen on 2019-09-22
what minimum usage value would expect to have?

---

### Post by TheFu on 2019-09-23
Some file systems lie about the true available storage.  **df -Th** would show the file systems too.

Sorry, I don't use timeshift, so cannot comment on that tool.

---

