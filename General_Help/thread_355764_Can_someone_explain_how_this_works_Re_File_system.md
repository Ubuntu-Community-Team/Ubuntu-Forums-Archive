---
title: "Can someone explain how this works? Re: File system"
date: 2007-02-07
forum: General Help
---

### Post by ardchoille42 on 2007-02-07
I am attempting to understand how the ext3 file system works and I have been told that disks don't get fragmented in Linux.

Consider the following scenario:

I create file1 on Monday and put about 50 bytes in it. I create file2 on Wednesday and put about 10 bytes in it. I create file3 on Thursday and put about 30 bytes in it. Assuming I create no other files, these files are on disk in the following order: file1 file2 file3

During the weekend I put 1Gb into file1, 400Mb into file2 and nothing into file3. I can't see how these files can remain in their original order (and have each file remain in one piece) on disk unless Linux allocates 1Gb for each file. Linux has to do one of two things:

1) Move files 2 and 3 so that file1 can contain 1Gb and remain in one consecutive file, move file3 so that file2 can remain in one consecutive file. This would require a lot of continuous "housekeeping" to keep all files in one piece since files are constantly being created and/or updated.

OR

2) Leave the original files where they are and put the "added" bits in a different place on disk with pointers to all the other bits so the file system can locate all pieces of a file. This would cause fragmentation of files.

Am I thinking wrong about how the file system works? Or do disks actually become fragmented and the statement "disks don't get fragmented in Linux" was false?

How is file fragmentation handled in Linux? Why do we not need to defrag disks in Linux? Is this where the journal comes into play? Does Ubuntu ship with a defrag tool?

---

### Post by llamakc on 2007-02-07
You may want to research inodes. Ext3 does rearranging  by design to avoid fragmentation. This is one of the benefits of using journaling.

---

### Post by fusiachi on 2007-02-07
Here's one [explanation]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting").  

I'm no technical expert, so I can't comment on the validity of this source, but it seems pretty logical.  It also suggests that your disk will become partially fragmented over time.  5-10% fragmentation seems pretty managable, and shouldn't dramatically hinder performance.

---

### Post by ardchoille42 on 2007-02-07
Thank you for the replies. From the dozens of articles I have read today, I have determined that, yes, an ext3 file system will become fragmented eventually, but never to the point of a major performance degredation unless your disk is 90% full or more. So, the answer to the fragmentation question is: "Unless your disk in 90% full, you don't have to worry about defragging it". And, if you install the newest Ubuntu release from CD each time it is released as stable, you won't have to ever worry about it anyway because the new install creates a pristine file system.

---

