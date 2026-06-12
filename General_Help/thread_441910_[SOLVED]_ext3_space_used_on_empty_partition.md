---
title: "[SOLVED] ext3: space used on empty partition"
date: 2007-05-13
forum: General Help
---

### Post by akudewan on 2007-05-13
I deleted two of my partitions: one vfat, and one ntfs, to make one larger partition (ext3). I just want to dump files temporarily in this one.

The total size of the partition is 5.2GB, but it shows only 4.8GB free. When I checked the partition, I found its totally empty, just a lost+found directory, which is also empty. Where is this space being used?

I understand that ext3 uses some kind of "journalling". Is this where is the space is being used? The purpose of this partition is to just dump files temporarily, my goal is to maximize the space available. Should I reformat it using a different filesystem?

---

### Post by 542 on 2007-05-13
ext3 partitions by default reserve space (~5% I think) for the root user. 

I believe this is done so that important processes running as root will always have some space to use if a user fills the partition up. Seeing as you're using the partition as a temporary store you won't need this reserved space.

To check this try running the following command:
```
sudo tune2fs -l <partition>
```

So an example would be:
```
sudo tune2fs -l /dev/hda2
```

Check what the 'Reserved block count' line says. tune2fs is a tool to modify ext2 and ext3 filesystem parameters so you should be able to set the reserved block count to 0 with the command:
```
sudo tune2fs -r 0 <partition>
```

Let me know how you get on :)

---

### Post by akudewan on 2007-05-13
Thanks mate! That did the trick. :)

Before:
```

Reserved block count:     69581
Reserved GDT blocks:      339
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)

```

After:
```

Reserved block count:     0
Reserved GDT blocks:      339
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)

```

It shows 5.1 GB free now.

---

