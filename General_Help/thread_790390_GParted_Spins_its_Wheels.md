---
title: "GParted Spins its Wheels?"
date: 2008-05-11
forum: General Help
---

### Post by nsivin on 2008-05-11
I use a desktop with a AMD-64 CPU, 2GB of memory, and a single 160MB hard disk, dual-booting Hardy (installed 4 days ago) and Win2K. Ubuntu is on a 117GB Ext3 partition, which I want to reduce considerably in size. There is also a 4GB swap file, which seldom seems to be needed. 

I have installed Gparted, and have no trouble starting it up. The problem is that it announces it is scanning all drives, and then just keeps scanning. I let it go for an hour, but it just keeps scanning, and doesn’t get to the stage where it reports on partitions. I am perfectly happy to let it run 12 hours, but I doubt that will accomplish anything. Any idea what is wrong, and what needs to be done about it?

---

### Post by Irony on 2008-05-11
Type in terminal;

```
gksudo gparted
```

See where it is getting stuck and post the results.

---

### Post by nsivin on 2008-05-13
When I tried the command in the last message, Gparted started up, scanned the disk for about 5 seconds, and showed the partition structure, ready for business. I then tried the utility directly, first by going to the System, Administration, Disk Partitioning menu item, and then in the terminal. It worked perfectly. Why it didn’t work in the first place, I have no idea. 

Thanks very much.

---

