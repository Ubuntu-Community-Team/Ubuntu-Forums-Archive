---
title: "My System Has Errors; How Do I Run Fsck?"
date: 2008-01-27
forum: General Help
---

### Post by apolloxi on 2008-01-27
Every time I start up, I always get this message (this is the contents of the error log):> 

Log of fsck -C -R -A -a 
Wed Jan  9 13:16:51 2008

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 1008 files, 482159/767600 clusters
open UUID=320D-180E:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5 contains a file system with errors, check forced.
/dev/hda5: Inode 640009 has imagic flag set.  

/dev/hda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 5

Wed Jan  9 13:17:32 2008
----------------

As you can see, for whatever reason, fsck always fails.

So, I tried to run fsck manually, but I always get a super scary message saying that the drive I'm trying to check is still mounted and I could kill my system by checking it while still mounted.

I tried poking around Ubuntu for something similar to "Error-checking" on Windows, but found nothing.

So, my question is, how do I run it manually without risking the death of my system, or without my system being mounted?

---

### Post by taurus on 2008-01-27
When you get that error message, it should drop you into a shell where you can run fsck by hand.

```
fsck -y /dev/hda5
```
Otherwise, boot from a LiveCD and run it from a terminal then.  Make sure you don't mount /dev/hda5 first before you run fsck on it.

---

### Post by apolloxi on 2008-01-27
All right. Thanks for the help.    ^_^

---

