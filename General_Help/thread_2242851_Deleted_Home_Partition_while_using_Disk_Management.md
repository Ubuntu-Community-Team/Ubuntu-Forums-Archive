---
title: "Deleted Home Partition while using Disk Management Windows 8"
date: 2014-09-04
forum: General Help
---

### Post by mj12 on 2014-09-04
I have a dual boot system on Dell XPS12.  Yesterday while using the windows 8 OS, accidently deleted one of the Ubuntu Partitions, which is now says Unallocated.

I can no longer boot into Ubuntu.  One EXT4, and One Swap Partition can be seen when going back to Disk Management on Windows 8.


I assume, the Home Partition is deleted.  Is there anyway to recover the documents.?  I tried to reinstall using the USB I used the first time.  I selected the Something Else option to prevent any additional  deletion, and it wants me to create a boot partition.   This is when I have stopped.

Thank you

---

### Post by adamitj on 2014-09-04
You'll need some pro assistance in order to recover your data when a partition is dropped. Basically, the data still on the physical disk, you must have dropped just the partition descriptor. If you want to give a try yourself, there are some opensource options available. Just google "Linux partition data recovery" and you get a lot of options.

P.S: I dunno if there are tools working with EXT4 already.

---

### Post by coffeecat on 2014-09-04
First thing - **Do not proceed any further with the installer**. If you install over your former home partition, now unallocated, you will reformat the space and make it unlikely you will ever recover the missing partition.

So long as you have not written to the area on the hard drive that formerly held your home partition, you will probably be successful in recovering the partition with testdisk run from a live Ubuntu session, either from a DVD or USB. Here are a couple of links for you:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

This following is rather old, but is written in a user-friendly way and introduces you to testdisk in a gentle way:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I repeat - **do not reformat the area of the drive where your home partition used to be**.

---

### Post by mj12 on 2014-09-04
Thank you both for your kind replies.  Unfortunately, while I was using the Disk Management Windows 8, I had extended the C partition by 20 GB.  It turns out that the 20 GB was taken from the 50 GB Ubuntu Partition that I had deleted and had become unallocated.

I have checked the internet and found the Linuex Reader, Diskinternals, that I downloaded and shows all the partitions, but any additional steps requires purchase of the rest of the downloaded software which is not clear that can help or not.

Also, I was wondering, whether removing the harddrive and using it as an external hard drive using another computer may help.  I don't have experience with solid state HD and not sure if there is any adaptor for connecting it to a USB port.

---

### Post by yancek on 2014-09-04
If you are trying to save data, use TestDisk which is available for free download and also, please read all the documentation you can before starting.  There is also a link on the page below to a Step-by-Step on how to use it.  It is not going to happen with a few mouse clicks, guaranteed.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by mj12 on 2014-09-04
Thank you all, Adamitj, Coffeecat and Yancek.  I am using the TestDisk, and have been able to recover some of the files, but I am not done yet,  looks good so far.  Appreciate your help.

---

### Post by mj12 on 2014-09-06
Okay!  TestDisk has one big issue:

It does not see the unallocated partitions.

Other issues:  

1.  It keep asking for more space for copying files.
2. The Doc and ppt files are all corrupted.
3. Some pdf files are recovered and most won't open, or have many pages missing.

I spent all day yesterday, selecting specific file formats or one file format at a time.

It may be best to re-install Ubuntu, but I guess I will delete everything once the unallocated partition is changed to EXT4.  Please note that the Swap and EXT4 partitions are okay.  Need to create boot and home partitions.

---

### Post by yancek on 2014-09-06
> It does not see the unallocated partitions.

Unallocated space is space that is not on any partition.  A partition should be formatted and have a filesystem on it.  Not sure what you mean here.
Are you copying to an external medium?

---

### Post by mj12 on 2014-09-06
The deleted partition shows as "unallocated" when looking at the disk space using Disk Management Windows 8.   It had the same size as when it was not deleted. However, you are correct when you say a partition cannot be unallocated.

---

