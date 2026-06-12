---
title: "Mysterious hard drive issue"
date: 2007-01-01
forum: General Help
---

### Post by lucas9000 on 2007-01-01
Background:

I have Ubuntu (Edgy) running dual boot on my AMD 64 machine (the other OS is Windows XP).  I recently completed a long-term project of ripping all my CDs to flac (using EAC in Windows, fwiw).  My machine has the following hard drives:

40 gb - this is partitioned in half and has the XP and Ubuntu on it.  I have the ext2 ifs driver/software installed in Windows so that Windows can read/write to my Linux drives.
300 gb - internal, formatted ext3.  This has my music on it.
300 gb - external, formatted ntfs.  This is the exact same drive as the 300 gb internal, but I put it in an external enclosure.  This holds a backup on my music on it.

My question relates to the two 300 gb drives.  They each contain a folder called "Music" that has all the flac files in it.  The Music folders on each are identical in size and their contents.  But, the drives also contain some other folders.  In the case of the external, it has a small folder (much less than 1 gb) containing some misc. software (flac, foobar2000).  The external also has the Windows "Recyled" (or whatever it's called) folder.  The internal has the "Music" folder, as well as "lost+found", "Recycled" (or whatever it's called), and I think another folder or two for Linux.  None of these miscellaneous folders contain much data...when I check the properties of each it's either 0 or much less than 1 gb.

The Problem:

When I look at the disk usage of the two drives, the internal (ext3) drive has 20 gb less free space than the external.  I can't find where that 20 gb is being used.  It's a complete mystery to me, and I wonder if anyone can help me figure it out.  Thanks in advance.

---

### Post by towsonu2003 on 2007-01-01
[Here]("http://www.mybroadband.co.za/vb/showthread.php?t=34219") I found this:
> 
The 5-8% is reserved for the superuser to use when space runs out, and also to maintain a space for better speed of operations and avoiding fragmentation.

I'm not sure about the details... 

This one seems to have the same issue: [http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

sorry, couldn't help too much.

---

