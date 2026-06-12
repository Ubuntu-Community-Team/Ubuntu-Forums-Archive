---
title: "[SOLVED] stop checking hard drive every 22 mounts?"
date: 2007-10-20
forum: General Help
---

### Post by stinkinrich88 on 2007-10-20
hello!

I have a 500gb drive full of DVDs and I don't want ubuntu checking it for errors at boot every 22 mounts. It takes ages. Any ideas how I can edit fstab to stop this?

thanks!!

---

### Post by mlind on 2007-10-20
If you're using ext2 or ext3 partition, you can change this with tune2fs tool.

To change fsck to check partition /dev/sdxy between every 40 mounts:
```

sudo tune2fs -c 40 /dev/sdxy

```

You can also define "time-dependent" checks, like days between fsck checks.

To check partition /dev/sdxy between between every 120 days:
```

sudo tune2fs -i 120d /dev/sdxy

```

Partition is checked if either mount count or time-dependent value is exceeded.
Read tune2fs manual page for more options (*man tune2fs*).


You can use fdisk to find out assigned devices for partitions (except if you're using device mapper)
```

sudo fdisk -l

```

---

### Post by seventyeights on 2007-10-20
Setting both -c and -i to zero should kill the checks cold.

```
sudo tune2fs -c 0 -i 0 /dev/sdxy

```

---

### Post by stinkinrich88 on 2007-10-20
hey guys, sounds perfect, thanks, but I get this error when I try to do either:

> tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.

any ideas?

thanks!

---

### Post by meierfra on 2007-10-20
sdb is the hardrive. You need to apply tune2fs to a partition.  So replace /dev/sdb   by  /dev/sdb1

(this assume that you only have one partition on sdb, otherwise you might have to  use sdb2 or sdb3 or ...)

---

### Post by stinkinrich88 on 2007-10-20
ahh perfect! thanks everyone!!! problem solved!

---

