---
title: "Re clonezilla"
date: 2013-11-23
forum: General Help
---

### Post by david98 on 2013-11-23
hi iv'e just discovered clonezilla and had a brief read up about it and thought it might be handy to clone 1 or 2 of my hdd's but i have a few questions for you guy's. I just downloaded the live version.

*1 has anybody here used it and how did they find it
*2 how quick is it at cloning I know it depends on hdd size and whatever but is it reasonably quick
*3 if you don't use it is there another programme that is equally as good or better

---

### Post by sammiev on 2013-11-23
I used clonezilla for years now and still do. I can save 3 OS in about 35 min. and restore at about the same.

---

### Post by speartip on 2013-11-24
I've used Clonezilla for about 3 years to backup & restore with no issues.
Transfer rates will obviously vary depending on your hardware. I generally get 3.5 - 4.5 gigs per minute.
One thing I have found though, is that I often need to run a file system check on the OS i'm backing up, otherwise Clonezilla throws out an error at the beginning.

---

### Post by The Spectre on 2013-11-24
You might want to check out Redo Backup & Recovery...
[http://redobackup.org/](http://redobackup.org/)

It has a clean interface and is very easy to use.

[IMG]http://redobackup.org/media/screenshots/1.jpg[/IMG]

[IMG]http://redobackup.org/media/screenshots/3.jpg[/IMG]

---

### Post by VMC on 2013-11-24
Fsarchiver is another, then the old reliable rsync or even tar. CZ and REDO both use Partclone to backup used sectors. You can use Partclone by itself. 
Two thing about CZ is the directory that it save the partition/disk to has a lot of usful info in there. 

Also be aware that you can't restore to a smaller partition, and you can't restore to another partition without some manipulations of the files. Partition by itself you can restore to any other partition as long as its the same size or larger.

Fsarchiver, rsync and others have the benefit of restore to smaller partitions. Only of concern it you need to restore to a different disk/partition.

As previously stated, its best to *fsck* the partitions before using CZ.

---

### Post by sammiev on 2013-11-28
Downloaded Redo Backup and used it to backup my full HD. Took about 40 mins to backup Windows and Linux. Will try to recover the backup to a larger HD. Then I will backup the bigger HD and try to recover it to a smaller HD. Guess I will be busy for the next day. :)

---

### Post by sammiev on 2013-11-28
Well going to the bigger HD went well. I had to redo the Windows MBR which went great. Then I booted from a live OS to get Ubuntu backup and running within the grub. All went very smooth and I have 2 twin HDs for my laptop. Time to backup this puppy and try to install the backup to a smaller drive. Should of added the restore from the backup with 2 OS took just less than 23 min.

Edit: Went to backup the clone HD and Redo Backup would not recognize the drive I'm using to post on at this time. Guess I will just keep on using Clonezilla. Attach is a screen shot of the clone drive using  GParted.

---

### Post by The Spectre on 2013-11-28
> **sammiev said:**
> Edit: Went to backup the clone HD and Redo Backup would not recognize the drive I'm using to post on at this time. Guess I will just keep on using Clonezilla. Attach is a screen shot of the clone drive using  GParted.
Bummer that Redo Backup & Recovery didn't work for every situation that you tried, maybe the next release will work for you.

For me it was Clonezilla that failed me, it works on my Desktop but not on my Laptop and the Laptop is quite a bit older hardware wise.

I tried both the 32 bit and 64 bit stable releases - 2.2.0-31 and the alternative stable releases - 20131125-saucy and none of them would work on my Laptop but Redo Backup & Recovery has worked flawlessly every time plus I like the clean simple interface.

That is what is great about having a choice because everything doesn't always work for everyone.

---

