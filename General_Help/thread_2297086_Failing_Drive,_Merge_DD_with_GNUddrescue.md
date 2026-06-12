---
title: "Failing Drive, Merge DD with GNUddrescue"
date: 2015-10-01
forum: General Help
---

### Post by braydon3 on 2015-10-01
Hoping someone can help me out. I have a laptop drive that was had 3 partitions, a ~67GB NTFS Partition, a ~23GB EXT4 root partition and a ~410TB EXT4 /home partition.
The drive started to fail, and I was busy at the time, so shelved it. Almost 2 years later, I needed some data so attempted to connect it to my computer. I then tried to create a copy using the DD command, and got 249.2GB before it failed. I then sat on the drive for a couple more months, then did some research and decided to retry recovering my data. When I connected the drive this time, my computer would not even post with it connected. However, if I connected it after boot, I could see in the system log that it got an identifier. In this case, /dev/sdd. It would not show up in disks, or in the file manager.
I then used GNU ddrescue, and managed to recover ~380 GB of the disk, with ~120GB of errors. 40% of that is in the first 250GB of the disk, which I believe, should be covered by my original DD image.

Is there anyway to merge my ddrescue image with the image created by DD?

---

### Post by sudodus on 2015-10-01
Welcome to the Ubuntu Forums :-)

What I know is possible is to run ddrescue with a log file, and to merge things found in later 'sessions' into the result of the previous sessions. This is described in the well written documentation at

```
info ddrescue
```

For example, maybe you can use the method described in the chapter '9 Generate-logfile Mode', or something similar.

You can also search for and try to recover files from what is already cloned by dd and ddrescue - try [photorec](www.cgsecurity.org). It works without a working file system (as long as it can find the file's data 'on the disk surface').

---

