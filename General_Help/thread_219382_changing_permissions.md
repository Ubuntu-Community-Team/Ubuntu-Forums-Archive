---
title: "changing permissions"
date: 2006-07-19
forum: General Help
---

### Post by deadkarma on 2006-07-19
i'd like to know how i can grant my account write access to my second hdd?  if anyone can help me i'd greatly appreciate it.  thanks in advanced

---

### Post by mlind on 2006-07-20
If it's a FAT32 or NTFS patition
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)


If it's a ext3 type partition, use /etc/fstab enry
```

/dev/xxx /mnt/share  ext3  defaults  0  2

```

where /dev/xxx is the filesystem. Then mount /mnt/share.

---

