---
title: "jfs partition disapeared"
date: 2007-07-26
forum: General Help
---

### Post by sloggerkhan on 2007-07-26
I have a jfs file system on an external drive that flat out won't mount and seems to have disappeared. GParted says it's still there, though it reports it as having about 1/2 the space used as it did. Is there some way to do a disk check/repair? And why won't it mount? It's on an external USB HD enclosure, typical seagate IDE hard drive, 250gb, which has 3 other partitions on an extended partition, all 3 of them are regular ext3, I just have the one jfs. Is there a way to force a disk check/repair, or something?

---

### Post by kevinlyfellow on 2007-07-26
You can use fsck after you install jfsutils

```
sudo fsck -t jfs /dev/{whatever}
```

---

### Post by sloggerkhan on 2007-07-26
Thanks. It said the filesystem is clean and it then started mounting. Kinda a funny, considering it wouldn't mount at all, before.

Edit:
After looking at this for a while it seems as though every time the jfs filesystem is unmounted, I must run fsck before being able to mount it again.

---

### Post by kevinlyfellow on 2007-07-26
I think I had a problem with the UUID for my jfs partition.  I can't remember the details though.  Do you mount it through UUID or the device name?

---

### Post by sloggerkhan on 2007-07-26
device name. Ideally I shouldn't have to... it is on USB external drive and my other partitions mount without having folders premade in in /media or being listed in fstab. (Their folders in media appear on the fly.)

---

### Post by kevinlyfellow on 2007-07-26
I haven't tried that scenario.  I think I'll give it a shot see if I have the same issues.

---

