---
title: "[SOLVED] how to resize (shorten) file on ext2 partition?"
date: 2008-07-01
forum: General Help
---

### Post by Selmi on 2008-07-01
is it possible to truncate file without creating temporary copy of it?

what i need to do is: i have several gb big file which is mounted as ext2 filesystem. it fills most of partition, but its not completely full of data. i want to use ext2resize to squeeze used blocks together and then free unused space of file to get more free space on partition. i don't have enough disk space to make another such filesystem big enough for everything so only possibility is to resize file itself.

is it possible? so far everything what i found was using temporary files :-(

---

### Post by VMC on 2008-07-01
I noticed that this is for "all variants", so  I don't know what your using, but in ubuntu gparted can handle the job. First output this command from a Terminal:

```
sudo fdisk -l
```

---

### Post by Selmi on 2008-07-02
gparted and fdisk work with partitions, not with files

but its already solved, i found one hint which seems to work, so for people who will need to do same task, use:
```

dd if=/dev/null of=file_to_truncate bs=xxxx seek=1
```
where xxxx is size you want to get after truncating

---

