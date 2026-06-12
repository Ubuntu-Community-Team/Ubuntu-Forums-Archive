---
title: "Hard Drive Partitions Fried on two Seperate Installs (Dapper and Feisty)"
date: 2007-05-15
forum: General Help
---

### Post by Legolover64 on 2007-05-15
Hey all,

I've tried installing Ubuntu on two separate machines. Several months ago, I tried this configuration with Dapper:

AMD Athlon XP 3200+
1024 GB RAM
160GB Western Digital HD SATA
ATI Radeon 9800PRO (AGP)

Install went fine, but when I wanted to allocate more space to Windows with PartitionMagic, it wouldn't let me, saying the entire harddrive was partitioned "BAD." GParted also came up with a similar error, and I was forced to reformat.

Then, more recently, I tried this configuration with Feisty:

AMD X2 64bit 4200+
2048MB RAM
250GB Seagate HD eSATA
nVidia Geforce 7600GT

And I had exactly the same problem. ext3 drivers didn't work, gparted didn't work, PartitionMagic didn't work. It's like Ubuntu fries every drive I try to put it on. As these are my only experiences with Ubuntu, I hope that this isn't a common problem. Both discs were shipped from Ubuntu.

Thanks in advance,
Peter

---

### Post by EmeraldTheMaster on 2007-05-15
**Edit: Nevermind**

---

### Post by wolf08 on 2008-02-10
Ubuntu didn't fry the drive, it just used a different partitioning scheme than partition magic expected. I had the same problems when I used to dual boot. The key is to only use one tool to create partitions. So, either make your partitions beforehand with PartMagic and then install Ubuntu or forget PartMagic entirely. In the case of the latter, if you want to shrink the ext3 partition, boot up with a livecd and use resize2fs ('man resize2fs' to read the manpage). Alternatively, use the partition manager (System -> Administration -> Partition Manager) already included on the disk. (Note - I think this might only be in Feisty and newer)

---

