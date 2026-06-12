---
title: "PartImage??"
date: 2007-03-26
forum: General Help
---

### Post by billdotson on 2007-03-26
Before I start, I use Linux and I like Linux but I play PC games sometimes so I keep Windows.  So please to not tell me the solution to my issue is to install Linux.  Moving on:

I was thinking of using PartImage to keep my Windows (NTFS) backed up in case I somehow get a virus, some major spyware or some type of error and need to replace it w/o having to reinstall all of my programs, reconfigure them and import all my files back.  I have ~20 PC games and those are a pain to reinstall and backup my save games.

Since my Windows install is NTFS I was wondering if it would work well enough to use it as a backup in case anything happened to my install.  On the partimage site it says that 

"The NTFS (Windows NT File System) is currently not fully supported: this means you will be able to save an NTFS partition if system files are not very fragmented, and if system files are not compressed. In this case, you will be able to save the partition into an image file, and you will be able to restore it after. If there is a problem when saving, an error message will be shown and you won't be able to continue. If you have successfully saved an NTFS NTFS partition, you shouldn't have problems as you restore it (except in the case of bugs). Then the best way is to try to save a partition to know if it is possible. If not, try to defragment it with diskeeper or another tool, and try to saving the partition again."

Does that mean all I have to do is to defrag before I do it?  Should I use the Windows defragmenter or should I use something like diskeeper like said on the partimage site?  Also, do I need to partition my Windows drive so there is just enough of a partition for my current Windows install?  Like if my internal HDD is 250GB, I have not partitioned any of it and I am using 150GB, should I resize (after defragging of course) to 151GB, then create a 151GB NTFS partition on my external HDD and then use partimage to back it up?

Also, I have an off-topic question related to defragging.  Say you partition your HDD so that there is only the minimal amount you need to get all your programs installed.  Would partitioning in that way keep the drive significantly less fragmented because NTFS doesn't have enough space to throw files around?

Thanks guys.  Also, if I can get this working routinely with NTFS I might use PartImage in my  PC tech support to backup customers installs :)

I have never heard of a partition copier before a couple weeks ago and partition copiers like PartImage or Norton Ghost are AWESOME.  I can't imagine I EVER spent an entire day getting my Windows reinstall configured again.  WOW HOW EASY!

---

### Post by aysiu on 2007-03-26
Since this is more support than discussion, I've moved your thread to General Help.

I think your best bet for backing up an NTFS partition is *dd_rescue* instead of PartImage.

Read more here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

