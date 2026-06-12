---
title: "Backing up o/s partition questions"
date: 2016-11-26
forum: General Help
---

### Post by ra7411 on 2016-11-26
When I installed Ub 16.04 I opted to separate the o/s from Home - separate partitions. This is a single desktop with 3 HDs and plenty of empty space. My o/s partition is 50gb, and about 24% filled.

I use Grsync to back up my Home files to a separate backup HD, and since I have a lot of empty space there, I'm thinking about backing up the o/s.

1) "Disks" program can create a partition image, but is that of any use if the o/s fails in a way that stops you from being able to boot up?

2) Clonezilla - I booted into it and looked through the menu sequences, but it seems to be oriented toward imaging the whole HD, I guess you have to use the "expert" menu option to be able to select a single partition, right?

     2.1) On the HD I'd be sending the o/s image to, do I have to create a partition for it to go in to? Does that destination partition have to be exactly the size of the source partition, or just bigger, or?

Any clarifying help, or even a walk through, will be much appreciated.

Thanks

---

### Post by speartip on 2016-11-26
Clonezilla will backup a partition without going into expert mode. The image size will only be the size of the used data on the partition as well. So a 30 gig partition with only 10 gig of space used will only be 10 gig in size. 
This may help:
[http://clonezilla.org/clonezilla-usage/general-live-use.php](http://clonezilla.org/clonezilla-usage/general-live-use.php)

---

### Post by TheFu on 2016-11-26
grsync is fine for a simple mirror, but there are other options to create versioned backups.  Lots and lots of other options.  zbackup, duplicity, rdiff-backup are just a few. There are many others.  The backup tool should manage the versioning for you and not require some funky, complex, file format to be used.

Image-based backups ... haven't used those since around 1999 for anything but Windows.  Very wasteful and I can restore a file-based backup on a unix-system in about 30 minutes, so why bother?  Guess it depends on what you know and how bonehead the restore has to be.

There are a mix of image/file-based backups possible using a tool like fsarchive (or fsarchiver, I forget the exact name). The cool thing about that tool is that empty space doesn't get wasted in the backup and it supports restoring to smaller partitions, provided the data fits.  That can be handy.

Image-based backups are hard to automate, since they need the disk being used not to be opened/live. That means downtime during the backup times. Can't have that.

i've written about my backup methods here A BUNCH, so won't repeat it. Would encourage you to find some of those posts. Some links in my signature too.

---

### Post by ra7411 on 2016-11-27
I did a Clonezilla backup of my o/s partition and the image is about 1/3 the byte size of the o/s.
Does that sound right, or is something screwed up? 
I don't think any compression options were selected, so I'm surprised at the size comparison.

---

### Post by howefield on 2016-11-27
> **ra7411 said:**
> I did a Clonezilla backup of my o/s partition and the image is about 1/3 the byte size of the o/s.
Does that sound right, or is something screwed up? 
I don't think any compression options were selected, so I'm surprised at the size comparison.

Sounds about right, Clonezilla will only backup the used blocks. not the whole disk.

By way of comparison my Xenial installation of 6GB has a clonezilla image size of 2.3GB.

Presumably you took the option to check the image ?

---

### Post by ra7411 on 2016-11-27
>[COLOR=#000000]Presumably you took the option to check the image ?<

Yes, and clonezilla said all was ok, but I was still a little askance at the difference.
But the size difference wasn't in partition size, just bytes in partition v. the clone size.
 That much shrinkage is pretty good.[/COLOR]

---

### Post by howefield on 2016-11-27
> **ra7411 said:**
> Yes, and clonezilla said all was ok,

Sounds like you are good to go then.

---

### Post by speartip on 2016-11-27
Somethings not quite right there. Clonezilla doesn't compress the data. The cloned partition should be equal in size to the amount of data used on thar partition. Check in your system monitor to see how much of the partition is used and compare that to the cloned image size.

---

### Post by TheFu on 2016-11-27
Test the restore. That's the only way to be certain that any backup is actually working in the way you need anyway.

---

### Post by howefield on 2016-11-28
> **speartip said:**
> Somethings not quite right there. Clonezilla doesn't compress the data. The cloned partition should be equal in size to the amount of data used on thar partition. Check in your system monitor to see how much of the partition is used and compare that to the cloned image size.

Default option is..

```
-z1, --gzip-compress Compress using gzip when saving: fast and small image file (default)
```

You can increase the compression or turn it off altogether.

---

### Post by speartip on 2016-11-28
@howefield. I stand corrected. I've been using Clonezilla for years to backup & restore, & only after checking now, have I realised that the cloned file is less than half that of the original.
 In that case the OPs file size appears to be about right.

---

