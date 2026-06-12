---
title: "Using dd to clone ext4 partition to ntfs partition"
date: 2013-12-27
forum: General Help
---

### Post by tdpham4 on 2013-12-27
Hello,

My storage drive is failing so I bought another hard drive to copy all my data over before it becomes corrupted. My failing storage drive has an ext4 partition for storing all my movies. On the new drive I want to copy my data over, I want to create a new partition in ntfs, then use dd to copy all data from the failing drive to the new drive. So here is the example of my command:

dd if=/dev/sda1 of=/dev/sdb1 bs=4096 conv=notrunc,noerror

I have used dd before to clone hard drive and partittion, but this is the first time that I have used it to copy data from one partition to another with a different files system. I just want to know if anybody has done this before, and whether the destination partition is corrupted after copying or not. I have also read that cp allows you to do this also but I am not that familiar with it. Last solution, I can just use copy and paste the data over but using that method to copy is slow and tend to damage the already failing drive.

If using dd is not possible, is there another possible solution? using cp? another program that I don't know about? Please let me know. Thank you and have a nice holiday.

---

### Post by mikewhatever on 2013-12-27
I'd suggest using rsync, cp or plain and simple copy/paste. All these should work, and copy just the data. On the other hand, dd is not the right tool, because it will copy data and the file system.

---

