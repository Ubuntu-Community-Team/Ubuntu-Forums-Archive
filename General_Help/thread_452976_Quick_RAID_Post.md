---
title: "Quick RAID Post"
date: 2007-05-23
forum: General Help
---

### Post by xela321 on 2007-05-23
Bet you'd never see those words together in a thread subject :smile:

I have a RAID5 array consisting of four 400GB drives:
/dev/mapper/sda1
/dev/mapper/sdb1
/dev/mapper/sdc1
/dev/mapper/sdd1

When I formatted the array, it reserved 5% for super user.  However, this is not the primary drive (which also has plenty of free space), so I'd like to reclaim that 5% for data storage, which would add an additional 60GB to the partition.

Are there any non-destructive ways to accomplish this?

---

### Post by fanatik on 2007-05-24
I believe, although I haven't tried it, that you can use tune2fs to adjust those parameters on your filesystem, so long as it's ext2/3. try:

```
$ sudo tune2fs -m 0 /dev/md0
```

or whatever your raid array is called. but, please ensure you have a backup first! :)

---

