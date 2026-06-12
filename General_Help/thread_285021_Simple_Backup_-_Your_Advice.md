---
title: "Simple Backup - Your Advice?"
date: 2006-10-26
forum: General Help
---

### Post by driggins on 2006-10-26
Greetings,

I have read as many guides on backup solutions as I could find. Thus far, I have gleaned the following
-there are lots of alternatives to accomplish the same thing
-this should be simpler than backing up my Windows machines

My goal: to completely backup my data partition, hdd1, which houses all data shared by my co-workers. I want to automate this process. To date, I have been using "cp" to copy the shared folder from my internal drive (hdd1) to my external, USB drive (sda1). I suspect there's a better solution.

My secondary goal: to do the same, complete, and automated backup for my installation of Ubuntu. This resides on hda. I would want the backup in case I screwed something up or the drive fails. I would do a complete restore and...voila!...my system is back in working order.

One solution I am experimenting with is creating a partition image using "dd". Here is the code I used:
```
dd if=/dev/hdd1 of=/media/backup/hdd1_partitionimage.dd
```
I have mounted sda1 as /media/backup. Any thoughts on this strategy?

As for automation, I am guessing figuring out how to implement a cron job is the thing to do.

Thanks for your feedback,

---

### Post by lloyd_b on 2006-10-26
First, your "dd" solution has an inherent problem:  If your disk drive dies, when you install the new one, the partition you create must be IDENTICAL to your existing one.  Using "dd" to restore to a non-identical partition could potentially create a non-usuable partition (remember, with that method you're not just backing up the files, you're backing up the superblock and other filesystem structures too)!

You could potentially use "cp -ru", which will recursively copy files, but only files which are newer than those in the destination directory (or which are missing from the destination directory.  This will reduce the amount of time required for the backup by a considerable amount.

If space is a problem, create a compressed "tar" on the usb drive.  "tar" also has a "-u" option, to replace files, but only those newer than what's in the archive.

Lloyd B.

---

### Post by driggins on 2006-10-26
Thanks for the tip on "dd". I did not realize the issue with regards to the physical drives. That idea has now been shelved.

I am testing "cp -ru" right now.

---

### Post by Beggar Su on 2006-10-26
Have you tried partimage to backup your partitions into an image file? I use it to make an image of my /home partition and ubuntu system to an external usb drive. I had a problem with setting up xgl/beryl and had a boot error. Luckily, I had my image file to restore the system.

---

### Post by driggins on 2006-10-26
Beggar,

Does partimage have the same restrictions (e.g. requires an identical physical disk) that llyod_b describes above?

---

### Post by driggins on 2006-10-26
lloyd,

Here's the test run I just executed:

```
cp -ru /media/data/Shared /media/backup/Shared
```

The "Shared" folder contains many sub-folders. I was expecting this process to copy some files not present on the "backup" drive. However, I am able to find folders that do not mirror the original.

Could this be some sort of permission issue? I am logged into Terminal as root while running this command.

---

### Post by lloyd_b on 2006-10-26
> Does partimage have the same restrictions (e.g. requires an identical physical disk) that llyod_b describes above?

First off - you do NOT have to have an identical DRIVE (though that would help).  You need to have a partition that's identical in size.  The raw drive (/dev/hda) is irrelevant - the partition (/dev/hda1 or whatever) is what's significant for that "dd" operation.  I *think* you can get away with restoring to a partition that's larger than the original, but the extra space will be lost after the restore (once you "dd" the image into that partition, the system can no longer access the space beyond the end of the original filesystem).

Note:  There *is* a safe way (without using any special software) to restore from a partition image (your ".dd" file).  That file can be mounted using a "loopback", and then the files copied from it using a "cp" command.

I probably wasn't clear enough - using "dd" to make the backup is okay.  It's using "dd" for the restore that you need to be careful of. 

---------------------------------

> Here's the test run I just executed:

Code:

```
cp -ru /media/data/Shared /media/backup/Shared
```

The "Shared" folder contains many sub-folders. I was expecting this process to copy some files not present on the "backup" drive. However, I am able to find folders that do not mirror the original.

Could this be some sort of permission issue? I am logged into Terminal as root while running this command.

What that command told the machine to do was "put a copy of /media/data/Shared into media/backup/Shared".  If you look, there's probably a "Shared" subfolder under "/media/backup/Shared" now.

Try this instead:

```
cp -ru /media/data/Shared/* /media/backup/Shared
```

This command tells the machine "put a copy of the contents of /media/data/Shared into /media/backup/Shared".

Please note that "cp -ru" (or a "tar" with the -u option) does not remove ANYTHING from the destination drive/file.  So, over time, the backup will gradually accumulate files that no longer exist in the original directory (I'll let you decide whether or not this is a good thing - I can make the argument either way....).

Lloyd B.

---

### Post by driggins on 2006-10-26
Ack! Syntax strikes again.

Thanks for your patience.

---

### Post by der_joachim on 2006-10-27
How about rsync? You can easily backup your /etc and /home partitions (or folders) with it. In the event of a crash or reinstall, you can easily restore your backup. Rsync is not incremental though. There's a few excellent threads on this forum with more information. 

I have also found a simple guide to generating a package list and reinstalling every package from that list: [http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564) .

---

### Post by PhrankDaChickenGeek on 2006-10-30
> **driggins said:**
> Greetings,

I have read as many guides on backup solutions as I could find. Thus far, I have gleaned the following
-there are lots of alternatives to accomplish the same thing
-this should be simpler than backing up my Windows machines

My goal: to completely backup my data partition, hdd1, which houses all data shared by my co-workers. I want to automate this process. To date, I have been using "cp" to copy the shared folder from my internal drive (hdd1) to my external, USB drive (sda1). I suspect there's a better solution.

My secondary goal: to do the same, complete, and automated backup for my installation of Ubuntu. This resides on hda. I would want the backup in case I screwed something up or the drive fails. I would do a complete restore and...voila!...my system is back in working order.

One solution I am experimenting with is creating a partition image using "dd". Here is the code I used:
```
dd if=/dev/hdd1 of=/media/backup/hdd1_partitionimage.dd
```
I have mounted sda1 as /media/backup. Any thoughts on this strategy?

As for automation, I am guessing figuring out how to implement a cron job is the thing to do.

Thanks for your feedback,

Its funny: I think you answered your own question. Download and use Simple Backup. It's in the package manager. I use it with an external HDD and once setup, I can forget about it!

---

