---
title: "Can lifetime_write_kbytes and &quot;iostat /dev/sdx&quot; be trusted?"
date: 2017-05-21
forum: General Help
---

### Post by jrmymllr on 2017-05-21
Ubuntu 16.04 64 bit here.

I've been trying to track down where the writes to my OS drive (a 32GB SSD) is coming from, so every 15 minutes I log the following:

```
cat /sys/fs/ext4/sdc2/lifetime_write_kbytes
iostat /dev/sdc|grep sdc
```


and I also log the output from ```
fatrace -t --filter=W
``` and use smartctl to check the SSD's reported total written data once in a while.

In general I've seen a steady, slow increase in writes; about 4MB/hour.  But this morning, across one of those 15 minute periods, lifetime_write_kbytes and the output from iostat both increased by 26,837,012.  If I'm correct, this translates into about 26GB which is insane, and nearly the size of the drive itself.  During this time nothing notable was happening.  This machine doesn't run a GUI, has no swap, df -h indicates no notable increase in usage, and things are set up to write as little as possible to this OS SSD. The counter retrieved by smartctl typically increases with each GB, and it didn't increase at all.

I haven't seen anything like this in the 4 or 5 days I've been doing this.  Is there any rational explantion for this?

---

