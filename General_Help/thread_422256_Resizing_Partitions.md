---
title: "Resizing Partitions"
date: 2007-04-25
forum: General Help
---

### Post by Sup3rkirby on 2007-04-25
hello.
I want to use a dual boot OS and to do this, I am supposed to have two separate partitions on my HDD, each one having a different OS on it, correct?
Well, on my laptop, stupid Acer, it came with a partitioned HDD.  It is a 60 GB HDD with two equal 30 GB partitions.

I wanted to create a smaller partition, and then resize the other one to make it larger, as that will be for my main OS, and the other, smaller partition will be for my secondary OS.

I tried using GParted, and this was run from my FreeSpire CD. I tried this because I know that when this CD boots, you have an option to partition your HDD.  It doesn't load the OS from the Live CD, just GParted.  When I tried to resize my main partition, it simply sits there with no progress.  I can't exactly do a clean install or anything and need to keep everything that is there, remaining there.

I have not tried my Xubuntu Live CD, but I'm pretty sure that has GParted on it, correct? If I were to start up Xubuntu from a Live CD and then run GParted at that point, would it work better(or at all)?

---

### Post by chakkaradeep on 2007-04-25
> **Sup3rkirby said:**
> 
I tried using GParted, and this was run from my FreeSpire CD. 

Try [GParted Live]("http://gparted.sourceforge.net/livecd.php") - a special live cd for partitioning :)

---

### Post by kagashe on 2007-04-25
> **Sup3rkirby said:**
> hello.
I want to use a dual boot OS and to do this, I am supposed to have two separate partitions on my HDD, each one having a different OS on it, correct?
Well, on my laptop, stupid Acer, it came with a partitioned HDD.  It is a 60 GB HDD with two equal 30 GB partitions.

I wanted to create a smaller partition, and then resize the other one to make it larger, as that will be for my main OS, and the other, smaller partition will be for my secondary OS.

I tried using GParted, and this was run from my FreeSpire CD. I tried this because I know that when this CD boots, you have an option to partition your HDD.  It doesn't load the OS from the Live CD, just GParted.  When I tried to resize my main partition, it simply sits there with no progress.  I can't exactly do a clean install or anything and need to keep everything that is there, remaining there.

I have not tried my Xubuntu Live CD, but I'm pretty sure that has GParted on it, correct? If I were to start up Xubuntu from a Live CD and then run GParted at that point, would it work better(or at all)?
Perhaps you have NTFS partitions and trying an old version of GParted.
Yes. Xubuntu Live CD has GParted and you can resize the partitions without going for installation.

kagashe

---

