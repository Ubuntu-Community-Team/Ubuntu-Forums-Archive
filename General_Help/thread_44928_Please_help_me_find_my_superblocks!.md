---
title: "Please help me find my superblocks!"
date: 2005-06-28
forum: General Help
---

### Post by slimsam1 on 2005-06-28
Here's the deal- I have a backup server and I originally made two ~100GB partitions on my 200GB drive. When I decided to delete the second one and resize the first to be 200GB, I didn't follow correct procedure and now I don't know the exact size that I originally made the first partition. I need this size so I can, in order:[list]
[*]find a superblock
[*]remove the ext3 journal
[*]use resize2fs to resize 100 to 200GB
[*]run tune2fs -o has_journal /dev/hde1
[*]be happy and sing folk songs
[/list]
Here's some output from my terminal play (in this output, the ~100GB filesystem is mounted while it lives in a ~200GB partition):```
root@jesus:/ # dumpe2fs /dev/hde1
dumpe2fs 1.35 (28-Feb-2004)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hde1
Couldn't find valid filesystem superblock.
root@jesus:/ # df /dev/hde1
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hde1             97656084  29277900  68378184  30% /archive
root@jesus:/ #
```

---

### Post by slimsam1 on 2005-06-28
Bump--can anyone help?

---

