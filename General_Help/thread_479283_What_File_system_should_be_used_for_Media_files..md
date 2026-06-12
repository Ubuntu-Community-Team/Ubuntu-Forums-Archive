---
title: "What File system should be used for Media files."
date: 2007-06-20
forum: General Help
---

### Post by azdragon on 2007-06-20
Here is a fairly straight forward set of questions that don't seem to have any clear answer in simple english.   

I have two hard drives, one is 250GB and one is 320.   

The 320 (sdb) 
sdb2  90gb ext3 for /
sdb5 200gb vfat for /media/content  (my mp3 files and my video files)
the rest of sdb is used for swap space and overhead

The 250 (sba) 
sda1 176gb   UNUSED SPACE
sda5  60gb  vfat for downloads

Ok here are the questions.   What is the best file system for sda1 if I want to do the following things
Store files larger than 4gb
Copy to and from with fairly fast speed

I don't need journaling, or permissions.   I read that ext3 is really slow, and you can not defragment, though that is usually not a problem.   I was thinking of reiserfs but after I made the drive that FS I kept getting permission denied when i tried to use it.

So should I just keep using vfat and if I really need to go over 4gb I will use my linux ext3 for a bit or is there some really great file system that I should try.   Thanks in advance.

---

### Post by david_edmundson on 2007-06-20
[I]I don't need journaling, or permissions. 
[/I]Journalling means that in the event of a crash/power cut none of the files being written to disk are lost. You probably want it. There's little overhead.

[I]I read that ext3 is really slow, and you can not defragment, though that is usually not a problem.
[/I]You can't defragment because you don't need to.  Ext3 is technically slower than ReiserFS particularly for small files (<1K). For normal usage, however, you won't notice any difference.

[I] I was thinking of reiserfs but after I made the drive that FS I kept getting permission denied when i tried to use it.
[/I]
Sounds like you mounted it "wrong". If you mount something as root, only root will have read/write unless you alter the permissions.

In short Ext3 kicks a lot of ***, only use FAT32 if you need a windows box to read it.

---

### Post by atria on 2007-06-20
I don't think ext3 is slow, the performance difference is definitely not noticeable unless you run a server.

If you really insist on using a filesystem that may offer marginally better performance for media files (movies, songs etc), use XFS which is designed for larger files.

Do note that you may lose data in the event of a crash/power shortage because of how XFS aggressively caches data (hence the reliability vs performance).

I personally recommend ext3 because of the reliability it provides.

Also there is no need for fat32 anymore even if you need to write to a windows partition. Check out ntfs-3g. 

Have fun

---

### Post by azdragon on 2007-06-20
Well I have never noticed ext3 to be slow, it is only what I read.  

The reason i don't need journaling is because I will only be storing large files on here after they are totally downloaded.  I will be copying them from another drive, so in the rare case that I get a power loss I will still have the original to go back to, the original is only deleted if the other is done correctly.

I may try XFS because the guy said it was good for larger files.   

I notice that if I boot on a gparted live cd I can make changes to the partition so I guess I just need to do that.  That is how i made all my others anyway.

---

