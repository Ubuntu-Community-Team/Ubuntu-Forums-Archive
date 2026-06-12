---
title: "AUFS only writing to first drive"
date: 2013-08-11
forum: General Help
---

### Post by z0mbi3 on 2013-08-11
I have a mix of 4 drives, making up a total of 5tbs but AUFS is only writing to the first drive in the mount command.

This is the command I'm using to mount:

```
sudo mount -t aufs -o br:/mnt/2TBa=rw:/mnt/2TBb=rw:/mnt/500GBa=rw:/mnt/500GBb=rw,create=mfsrr:20971520,sum none /mnt/combined
```

So the mount is visible and working, but 2TBa is the only drive being written to. It fills up, then the combined mount stops working and shows "invalid device" when I run ls on it.

Any ideas?

---

### Post by demslam on 2013-08-27
Howdy. I believe you want to set your create to create=mfs only. 

```
sudo mount -t aufs -o br:/mnt/2TBa=rw:/mnt/2TBb=rw:/mnt/500GBa=rw:/mnt/500GBb=rw,create=mfs,sum none /mnt/combined
```

I believe you are adding round robin when you have the rr which may not be needed.

[http://manpages.ubuntu.com/manpages/lucid/man5/aufs.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/aufs.5.html)

---

