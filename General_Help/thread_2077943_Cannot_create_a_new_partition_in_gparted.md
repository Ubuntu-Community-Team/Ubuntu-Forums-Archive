---
title: "Cannot create a new partition in gparted"
date: 2012-10-29
forum: General Help
---

### Post by erkaninho on 2012-10-29
I have dual-booted my laptop with Windows 7 and Linux Ubuntu. And I shrank my Windows hard drive 2GB, so I have 2GB of unallocated space on my hard-drive. Which I want to allocate using ext3 file system, and I will use it for my LFS (linux from scratch) project. But it says that I already have 4 primary partition and that I cannot create a new one. I have seen over the Internet that I have to create an extended partition and put it there, but it simply doesn't allow me to create any kind of partition at all. If you could tell me how can I do it, with step by step guide I would be glad. I also upload a screenshot of my current situation in gparted.

---

### Post by jerrrys on 2012-10-29
sda3 is your extended partition so resize sda3 to include the1.95G and put LFS in the extended partition.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

---

### Post by grahammechanical on 2012-10-29
For some reason, decided back in the mists of time we can only have 4 primary partitions on the hard disk. There is a system being put on the latest machines that overcomes this but it brings it own problems with dual booting.

Microsoft has used up the allocation of 4 primary partitions. I believe that I am correct in saying that you have to delete one of those primary partitions and then create an Extended partition, which is a special kind of primary partition. You then create inside the extended partition any number of logical partitions that you have space for.

But if you have been able to install Ubuntu then you will already have an extended partition because Ubuntu needs a minimum of two partitions.

That is the way to do it.

Regards.

---

