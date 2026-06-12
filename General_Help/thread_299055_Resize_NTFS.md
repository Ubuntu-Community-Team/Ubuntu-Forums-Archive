---
title: "Resize NTFS?"
date: 2006-11-13
forum: General Help
---

### Post by serlex on 2006-11-13
I would like to shrink my ext3 partition and add it to my NTFS partition. I have tried g parted, but will not let me do it!

---

### Post by taurus on 2006-11-13
Did you run gparted from Ubuntu or from the LiveCD?  You need to run it from the LiveCD since gparted can't resize partition that is currently being used.

---

### Post by serlex on 2006-11-13
yes through LiveCD! i cut out 10GB of ext3, but can not extend NTFS, can only shrink it!

---

### Post by taurus on 2006-11-13
And both partitions for NTFS and ext3 are right next to each other, right!  What's the output of this command, from a terminal then?

```
sudo fdisk -l
```

---

### Post by Jongi on 2006-11-13
I think it is always best to do any filesystem work on an ntfs partition in windows. And I think to a large extent linux assumes the same.

---

### Post by groggyboy on 2006-11-13
i believe that is a limitation of the NTFS file system and gParted...

It is possible to move and resize fat32, on the other hand.

Is the ext3 partition *before* the NTFS partition?  If it is, I'm afraid you are out of luck.  Because I'm fairly certain the only way to resize an NTFS partition is to add to the *end* of it.

---

### Post by serlex on 2006-11-13
hmm, i so need to do research more, wasnt so hard after all, copied ext3, created 10gb, paste ext3 into it, and grow NTFS

thx

---

### Post by Jongi on 2006-11-13
It's only recently that write support to an ntfs partition in linux has been relatively stable with ntfs-3g. Look also to the fact that the mkfs and fsck commands have no ntfs support. It is clearly pointing you to do whatever partitioning you are wanting to do in windows. I suppose there is the risk that windows will want you to delete the ext partition. But when I used to run windows, I think there was most likely a program which allowed to create/resize.

---

