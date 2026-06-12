---
title: "GPT Partition table - undetectable corrupted or deleted?"
date: 2014-03-08
forum: General Help
---

### Post by eyeJ on 2014-03-08
Hello I have a problem with a hard drive containing backup data.
I am pretty sure that it was formatted with a GUID partition table and ext4 filesystem.

Previously I used it without problem for over a year to backup my data with clonezila.

But suddenly today it shows that the drive is not formated at all. I suspect that the data is still intact because i had similar problems with windows drives. Which just needed a repair of the partition table.
I have searched google and ubuntu forums and found that it is best to ask for your particular case so as not to make things even worse.

The only info I can provide so far is that the drive once I open gparted reports the folowing warning (red dot with "!" sign near unallocated text):
invalid argument during seek for read on /dev/sdb

How can this be fixed?

---

### Post by The Cog on 2014-03-08
I would probably use the command 
```
sudo parted -l
```
to see what's there. But I don't like the look of that error message. That looks scarily like some kind of hardware error.

---

### Post by eyeJ on 2014-03-08
Thanks for your suggestion... :)
I tried parted -l

I get the same error for /dev/sdb:
Invalid argument during seek for read on /dev/sdb

I would like to backup the partition table before i try anything potentially destructive.

I tried the following command:
sfdisk -d /dev/sdc > parts.txt
but it says that it doesn't work on GPT drives

Here is where i got this command:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Any suggestions are appreciated!

---

### Post by oldfred on 2014-03-08
With gpt drives you need to use gdisk or sgdisk not fdisk.

Have you used Disks or Disk Utility to look at drive's smart status. It can run lots of tests, but all I know is passed is good and anything else is time for a new drive.

sudo apt-get install gdisk

       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by eyeJ on 2014-03-09
I tried gdisk (actually I was using sgdisk with gdisk commands and confused my self)
I did manage to make a backup of the partition table with sgdisk before I started messing around.
Automatic repair seems to think that the best partition table was the one that contains no partitions.
Tried reloading from backup, but it complains that the partition is to large for the drive.
This is the same error it reported when I used the -v option. Because of this size issue it refuses to
load from backup so I'm stuck.

There were 4 errors in total when i used the -v option first time: (but unfortunately I don't remember them all)
there was one error it said would be fixed automatically when it saved the tables to disk
there was this size issue
and some kind of alignment issue
maybe an overlap issue

Now when I use the -v option it says that the partition table is ok and that there is only free space.

Started recovery with gparted and hopefully it will find the partition before I grow a gray beard.

Guess the best option now is to wait for gparted. It's a 3tb drive so I hope it doesn't take a week to find.
If someone knows how to repair this partition issue please share :)

---

### Post by oldfred on 2014-03-09
You can also try testdisk. It works on both MBR(msdos) or gpt drives, you choose at startup. 
Scan of very large drive could take days.

Do you know exact start and size of partition(s) on drive. The procedure for overlapping backup partition table is to delete last partition and recreate it just a few sectors smaller. I think start has to be same or else you lose data.

 last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vitial just in case.

---

