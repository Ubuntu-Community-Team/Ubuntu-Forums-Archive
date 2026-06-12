---
title: "Slow system when using disk"
date: 2008-06-18
forum: General Help
---

### Post by larini on 2008-06-18
Hi, I have two HDs 250 GB.
I perform a file copy with 4GB from one disk to other.

During copy, the system is very low responsive. The firefox takes about 30 seconds to start. The problems seams to be in starting programs.

What could be this ?

---

### Post by cmnorton on 2008-06-18
It is hard to tell without knowing something more about your system's hardware.

---

### Post by larini on 2008-06-18
Ok.

Mobo: intel dg965wh
CPU: core2duo 6600
HD: 250GB seagate 7200rpm
memory: 2GB 667mhz

---

### Post by larini on 2008-06-18
This is normal ?

---

### Post by larini on 2008-06-19
I will try another linux to make a benchmark.

---

### Post by cmnorton on 2008-06-19
> **larini said:**
> Ok.

Mobo: intel dg965wh
CPU: core2duo 6600
HD: 250GB seagate 7200rpm
memory: 2GB 667mhz

It seems like you have a perfectly good enough system with enough RAM. The disk is probably SATA, right? Look at the output from top and ps, and see what else is going on.

I have a fast dual-core 2.4 GHz, 7200 RPM SATA, and 2GB RAM. There are some tasks that lay the system low, and that's not Kubuntu's fault. 

These tasks are usually disk i/o intensive, like importing a 1.3 GB database, which is I/O intensive, even more than an export (Informix SE). During this time (about twenty minutes, other commands are sluggish. 

There have been a lot of articles lately -- Linux Journal -- about solid state disks. They improve speed a lot at more cost. Usually I/O is the speed roadblock.

However, it would be helpful to know what else is running on this system.

---

### Post by larini on 2008-06-19
I have a fresh install of 8.04. There is nothing running, just file copies.

My partition is ext3. Raiserfs is better speed or same thing?

---

### Post by cmnorton on 2008-06-19
As I understand it, Reiser is more optimized for small files. I do not know how that would affect your file access speed.

---

### Post by ccc1 on 2008-07-27
> **larini said:**
> Hi, I have two HDs 250 GB.
I perform a file copy with 4GB from one disk to other.

During copy, the system is very low responsive. The firefox takes about 30 seconds to start. The problems seams to be in starting programs.


hi,

i have exactly the same problem. Have you solved it? 

ccc1

---

### Post by Spokey on 2008-07-30
> **larini said:**
> I have a fresh install of 8.04. There is nothing running, just file copies.

My partition is ext3. Raiserfs is better speed or same thing?
larini, I wouldn't go for ReiserFS, it's very slow. Have you tried putting the Informix data on an ext2 filesystem?

---

