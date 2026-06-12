---
title: "PartImage backup"
date: 2007-01-23
forum: General Help
---

### Post by carverj on 2007-01-23
Hi all,
         If I have a 13G partition and want to copy the 4G of information on it (Ubuntu and personal stuff), will PartImage allow me to copy just the 4G?
You see without an external drive I cant spare the space and so would like to copy the information to the small amount of space I have on slave and then burn to DVD.
Hope this makes sense
Thanks

---

### Post by aysiu on 2007-01-23
PartImage backs up only the space used--not the entire partition. In other words, from [the official PartImage site](http://www.partimage.org/Main_Page): > Partition Image will only copy data from the used portions of the partition. For speed and efficiency, free blocks are not written to the image file. This is unlike the 'dd' command, which also copies empty blocks. Partition Image also works for large, very full partitions. For example, a full 1 GB partition can be compressed with gzip down to 400MB.

---

### Post by carverj on 2007-01-23
> For example, a full 1 GB partition can be compressed with gzip down to 400MB.

Cool, that would be really handy for people who only have a CD burner!

---

