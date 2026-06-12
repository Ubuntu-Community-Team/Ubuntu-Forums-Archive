---
title: "ddrescue for a single partition"
date: 2014-09-09
forum: General Help
---

### Post by pesco on 2014-09-09
Hello,

I need to backup /dev/sdb1, which is a 150GB NTFS partition on the corrupt 1TB /dev/sdb.

```
ddrescue -v /dev/sdb1 /mnt0/sdb1.img /mnt0/sdb1.log
```
/mnt0 being the mount point of /dev/sda1 (1TB ext2 partition on the new 1TB drive I want to store the backup on).

I expected ddrescue to only copy /dev/sdb1, but it's going on to write an image of the whole disk
```
ddrescue -v /dev/sdb1 /mnt0/sdb1.img /mnt0/sdb1.log

About to copy 1000GBytes from /dev/sdb1 to /mnt0/sdb1.img

```

About 400GB where rescued so far (without errors).

fdisk -l shows all partitions correctly, so I don't think the partition table was damaged?

Is this the correct behavior? Then how is it possible to ddrescue 'sdb1' only?

Thanks!

---

### Post by pesco on 2014-09-09
ddrescue crawled to an halt, after a while it finished with an error stating there was no more room to write on.

I'm trying a different approach now:
```
# ddrescue -v /dev/sdb /dev/sda sdb_log
```
It should clone what's left of /dev/sdb on /dev/sda, they're both 1TB, and then I should be able to work on the copied data. Can anyone confirm please?

Sorry but I have quite a bit of anxiety about this, and as much as I would like to read the full documentation I have other work to do and still get the important files to safety by the end of the day.

All help appreciated, thanks!

---

### Post by J_Me on 2014-09-09
To speed things up you should run ddrescue twice, once with -n and then a regular pass. Also you should repeat the pass at least a few times with -r3 to make sure you've captured as much as possible. You need to create a .logfile to do this.
So for example if you know the names and paths of the files you want to rescue you could try for those first.
first pass```
ddrescue -n -r3 /dev/sdb1/path/to/the/file/fileName.jpg /dev/copyToThisDrive/fileName.jpg fileName.logfile
```secon pass```
ddrescue -r3 /dev/sdb1/path/to/the/file/fileName.jpg /dev/copyToThisDrive/fileName.jpg fileName.logfile
```Or if for example you only used 5gigs of space on that partition, use -s5000000000(bytes) to stop rescuing after 5gigs.
first pass```
ddrescue -n -s5000000000 -r3 /dev/sdb1 /dev/copyToThisDrive/part.img sdb1.logfile
```second pass```
ddrescue -s5000000000 -r3 /dev/sdb1 /dev/copyToThisDrive/part.img sdb1.logfile
```
In brief
-n = no split, use this to speed up the rescue process
-i = starting point, leave this out if you want to start from the beginning of the partition. e.g -i1000000000 from the first 1gig
-s = how much of the drive you want to rescue. -s5000000000 would stop after the first 5gigs.
-r3 = use this if you want to repeat the process three times then quit, or -r-1 for indefinite repeats until you manually quit with ctrl+c.
-d = bypass kernel cache
-b = block size


For anyone else reading this
'/dev/sdb1/path/to/the/file/fileName.jpg /dev/copyToThisDrive/fileName.jpg' and '/dev/sdb1 /dev/copyToThisDrive sdb1.logfile' are just an example and not to be used.

---

### Post by pesco on 2014-09-11
Thanks J_Me, Excellent advice, I'm going to translate it in my other post on the Italian Ubuntu forum for those in need. Too bad my own brute attempt at cloning the whole drive with all the errors worked fine ;)

(Apparently only some System files were lost, but Windows Recovery took care of that.)

---

### Post by pesco on 2014-09-11
One thing is not very much clear, sorry if it sounds dumb: it doesn't look like the destination disk need formatting prior to the rescue, or it would need to be mounted too and it's path would not be in /dev, is that right? So if I tried to rescue fileName.jpg to /dev/copyToThisDrive/fileName.jpg, would it be placed at the very beginning of the disk? Overwriting the partition table if there was one?

Thanks again!

---

### Post by J_Me on 2014-09-11
My mistake(and it's a big one) thanks for pointing that out. I should have said '/home/yourName/copyToThisDrive/fileName.jpg' where 'yourName' is what you logged in as and not '/dev/copyToThisDrive/fileName.jpg' in the example as it's just a single file that's trying to be recovered.

In your example 'ddrescue -v /dev/sdb /dev/sda sdb_log' you'll be copying/mirroring/cloning the whole disc 'sdb' including the partition table as well as the files to the whole disc 'sda' so any partitions/files on 'sda' can't be mounted and will be overwritten.
When working out the right paths I use 'cat /proc/partiotions' and 'mount' to make sure I'm copying to the right places. 'cat /proc/partiotions' is useful as it lists all discs connected to the computer whether they are mounted or not.

From the ddrescue man page 'info ddrescue'
```
Example 1: Rescue a whole disc with two ext2 partitions in /dev/hda to/dev/hdb.
Note: you do not need to partition /dev/hdb beforehand, but if the
partition table on /dev/hda is damaged, you'll need to recreate it
somehow on /dev/hdb.


     ddrescue -f -n /dev/hda /dev/hdb logfile
     ddrescue -d -f -r3 /dev/hda /dev/hdb logfile
     fdisk /dev/hdb
     e2fsck -v -f /dev/hdb1
     e2fsck -v -f /dev/hdb2
```Hope this helps

---

### Post by pesco on 2014-09-12
Awesome. I'm recovering everything now, ancient IDE drives and scratched CDs. Thank you sir, you've been very clear.

---

