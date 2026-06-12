---
title: "Renaming, Reformatting, &amp; Partitioning HDDs"
date: 2007-12-23
forum: General Help
---

### Post by money2themax on 2007-12-23
just as the title says i need to know how to reformat, Partition, and rename HDD not the main one but my 512MB Flash Drive, 200GB SATA HDD, & 120GB Pocket HDD

---

### Post by p_quarles on 2007-12-23
The easiest way is to use the Gparted application, which will allow you to do all of these things. It's in the repositories, so you can install it by searching in the Synaptic Package Manager.

This method will work for any of your "extra" drives -- i.e., those beside the one your OS is installed on. The reason for this is that the drive needs to be unmounted when you are partitioning it.

If you ever need to repartition your primary hard drive, you should get the Gparted Live CD (from sourceforge.net). That way, you can run the partition editor from the CD, without having the main drive mounted. 

Anyway, if you've ever done partitioning with Windows, Gparted should seem pretty familiar. The main difference is setting mount points. Feel free to ask away about that if you need any help.

---

### Post by money2themax on 2007-12-23
yeah i've formatted on windows XP before if it's anything like that i should be set but i'll come back if there is any hiccups in the process

---

### Post by money2themax on 2007-12-23
sry I'm not trying to bump this topic but this is a new thought it is taking forever for Gparted to find all of my drives what is wrong?

---

