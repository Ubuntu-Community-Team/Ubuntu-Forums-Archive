---
title: "Mounting partitions in file"
date: 2007-03-14
forum: General Help
---

### Post by lean on 2007-03-14
Hi, 
I have a Qemu image as a file, but I cannot mount the partition.

fdisk hd.img, and pressing p gives:

Disk hd.img: 0 MB, 0 bytes
128 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes

 Device Boot      Start         End      Blocks   Id  System
hd.img1   *           1         887     3576352+   7  Linux

So how can I get hd.img1 created as a device, or get it out otherwise? I cannot mount hd.img directly, since the bootloader is in the way.

---

### Post by lean on 2007-03-14
Okay, found the answer:
[http://www.clarkson.edu/projects/itl/honeypot/ddtutorial.txt](http://www.clarkson.edu/projects/itl/honeypot/ddtutorial.txt)

I googled for create device fdisk

---

