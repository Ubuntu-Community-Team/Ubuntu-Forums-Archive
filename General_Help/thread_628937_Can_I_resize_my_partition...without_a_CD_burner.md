---
title: "Can I resize my partition...without a CD burner?"
date: 2007-12-01
forum: General Help
---

### Post by WarMonkey on 2007-12-01
Is there a way to resize my Ubuntu 7.10 partion without a live cd (or any cd)? 

I used unetbootin to install Ubuntu on my laptop (just to try it out), but I only gave it 6 megabytes to use. I am able to access my Windows partition, so if there is no way to resize my ext3 partition, how do I move my Home Folder to another location?

Also, I have Partition Magic installed on my Windows partition, but from what I read it doesn't seem to recognize anything other than FAT and NTFS.

---

### Post by Craigus on 2007-12-01
Unless it is an ancient version of Partition Magic, it will recognise and work with linux partitions with no problems.

---

### Post by WarMonkey on 2007-12-01
Well, I just loaded Windows and opened up Partition Magic; you're right, it does recognize that its an ext3 partition. The only problem is that it won't let me do anything other than delete it.

Any other ideas?

---

### Post by Craigus on 2007-12-01
What version of PM is it ?

---

### Post by Craigus on 2007-12-01
An alternative is to use some like :

[http://www.diskinternals.com/linux-reader/]("http://www.diskinternals.com/linux-reader/")

to access the ext3 partition within windows.

---

### Post by WarMonkey on 2007-12-01
I have Partition Manager 8.0, I'm going to try the link.

---

### Post by WarMonkey on 2007-12-01
It's a nice tool to have, but I want to be able to install large deb packages from Ubuntu and not run out of space (I only have 986 mb left).

---

### Post by Craigus on 2007-12-01
I thought you wanted to recover your /home data and then resize the linux partition.

Can you use linux reader to get and save the data to your windows partition and then either PM in windows or the partitioner after netbooting to delete / resize the linux partition ?

---

### Post by p_quarles on 2007-12-01
Does this laptop have the ability to boot from a USB drive? If so, there are ways to put a CD image on a flash drive and boot from that. 

You actually *can *run Gparted from the hard drive. The catch is that you can't manipulate a partition that is currently mounted. If nothing else works, you might be able to do this:
1) Unmount the Windows partition
2) Use Gparted to shrink it
3) Use Gparted to create a *new *partition. You could mount this new partition as your home folder. 

The one thing you *cannot* do, though, is use Gparted to increase the size of the partition from which it is currently operating. 

Definitely look at the USB drive option first, though. That will be the safest bet. If you can buy/borrow an external CD drive, though, that would be the easiest solution.

---

