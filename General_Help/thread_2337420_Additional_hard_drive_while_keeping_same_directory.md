---
title: "Additional hard drive while keeping same directory structure, symbolic links?"
date: 2016-09-17
forum: General Help
---

### Post by bboughton on 2016-09-17
I have a bunch of python scripts which automate much of my remote sensing processing tasks.

The situation is, I am running out of disk space and want to add another hard drive but in doing so I want make it appear to my python scripts that all the files are still organised and able to be searched in the same directories.

Would it be a suitable solution to create a storage folder on the new disk drive. Whenever my scripts generate a new file they store it on the new disk and then generate a symlink to where I would have liked it stored if I had the capacity to do so, therefore retaining my existing directory structure?

Has anybody got any other suggestions?

Cheers,
Ben

---

### Post by TheFu on 2016-09-18
yes. you can do this. Why not just mount the extra storage where you want it and avoid the symbolic links?

Be certain you have enough backup space to support any new storage added too.  If the data is important enough to have, then it is important enough to backup.

---

### Post by bboughton on 2016-09-18
> **TheFu said:**
> Why not just mount the extra storage where you want it and avoid the symbolic links?

This is the exact advice I needed. I'll give it a go. 

So I can mount to a directory that already has files in it? How does the OS choose which device to write the file on to?

---

### Post by TheFu on 2016-09-18
Try it and see what happens.  If it doesn't do what you want, umount it and try again.  10 sec to mount. 10 sec to look around. 10 sec to umount, if you don't like it.
Experience is the best teacher, right?

---

### Post by mcduck on 2016-09-18
Mounting something over a non-empty directory will hide the previous contents. They'll still exist on drive but will be inaccessible (and of course also use disk space).

What you'd probably want to do is first move all the files to the new drive, and *then* mount it in the same place.

---

### Post by bboughton on 2016-09-19
OK thanks. I want to use both drives and keep same structure. I am now thinking again that symbolic links may be the way to go if mounting on an existing directory hides original files.

---

### Post by TheFu on 2016-09-19
You can keep the same structure easily. It is just about having access to the storage.  Are both partition formatted with Linux-file systems? then there aren't any restrictions.  If a non-Linux file system is being used (ntfs/exfat/fat32/....), then you can only have "data" on that disk because the file permissions aren't manageable per file.

If you provided more details, we might have better advice.  I've mounted partitions in all sorts of places over the decades - even over existing directory structures (good way to prevent losing files). Generally, mounting a partition to an empty directory is what most people want.  It is trivial to move files and retain the complete permissions, ACLs and structure, just use rsync or tar to move everything.  As long as the files and directories are mounted where the OS thinks they belong, the actual storage used doesn't matter.

---

### Post by bboughton on 2016-09-19
Thanks for your input.

OK so more information is that I use out-of-db rasters in a POSTGIS enabled Postgresql database. I cannot move the existing files without modifying a database which is being accessed all the time. I want to continue saving the raster files to the current directory but my hard drive is running out of space. I don't want to and can't move the files to a new disk as I want to keep using my current disk with the second disk be an expansion not replacement. Also to complicate matters, once files reach a certain age they will be deleted so space will free up on the existing disk from time to time.

Both will be with Linux file system.

---

### Post by HermanAB on 2016-09-19
This one of the problems that LVM, btrfs and zfs address.

---

### Post by TheFu on 2016-09-19
That does make sense. Would be smart to modify the code to place non-DB files into daily/weekly/monthly grouped directories. That way, you'll always have a split and can swap in/out mounts as needed.

What about weekly maintenance periods for patching?  If you don't have those already - start negotiations ASAP.  No system can run without maintenance.  Predictable downtime is better than unpredictable downtime. 

You can move everything to the new disk and mount it in the old location. Just need the time to move everything. That way the files all appear to be in the same location.  Plus, if you make the new disk with LVM and LVs, then you can add more and more and more disks and extend the LV on the running file system.  Just be certain you do the same with your backup areas. 

This all comes down to pay-me-now or pay-me-later decisions. It is "later." ;)

---

### Post by bboughton on 2016-09-20
OK thanks for this information, it has been helpful for me to think through this. I think I know my options now. It is definitely 'later'. One of those times when I thought 2tb would be 'enough'.

I think have a solution similar to your suggestion about grouping files and swapping mounts in and out, it's not prettiest but should work.

My next design will use LVM.

---

### Post by Bucky Ball on 2016-09-20
If you're happy with the outcome, please mark the thread as solved to help others. This will *not* close the thread to further discussion. It will save potential helpers time and hopefully provide clues to those searching for them. Thanks and good luck with it. :)

---

### Post by Skaperen on 2016-09-20
i use btrfs.  it and a couple other filesystem types let you merge more partitions into a joint filesystem.

---

### Post by TheFu on 2016-09-20
> **bboughton said:**
>  My next design will use LVM.

LVM isn't the only answer.  ZFS can do it too and so can a few other file systems, though I consider those experimental still, like btrfs. 
Just be certain you have a way to backup all that data if spanning physical disks is where you go.  I lost 80% of my data thanks to 1 HDD failure on a file system that spanned 3 physical HDDs. All the data on all 3 of them was lost - and I wasn't striping.

---

