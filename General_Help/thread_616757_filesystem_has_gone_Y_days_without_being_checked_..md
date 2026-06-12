---
title: "filesystem has gone Y days without being checked ..."
date: 2007-11-18
forum: General Help
---

### Post by endfx on 2007-11-18
Hi,

Every so often I have to reboot a server and sometimes I get a message similar to:
"filesystemX has gone Y days without being checked. Check forced"

And then does a full filesystem scan. I'm using ext3 so this can take some time (I should start using XFS or something). 

My question is, what defines how many days until a check is forced? Where is this specified? If I have to reboot a server and need it back up, I can't wait  for the filesystem to be checked. Can I turn this off somehow?

Thanks!

---

### Post by V-600 on 2007-11-18
You can alter the file /etc/fstab so as not to scan various partitions at start up. Off the top of my head I can't remember if its the fifth or sixth column that is responsible, but you change it from a 1 to a 0.

From;

 [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
"The 6th column is a fsck option. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem."

---

### Post by atlfalcons866 on 2007-11-18
you change it by every certain amounts by doing

sudo tune2fs -c x /dev/whateverharddiskpartition you want  to change.

Where x is the amount of mounts.

you can turn off fsck by doing sudo tune2fs -c 0 /dev/whateverharddiskpartition 
But keep in mind if the kernel detects corruption or inconsistency it will still force fsck.

I wouldnt use XFS it gets corrupted to easily.

for more info do this at the terminal

man tune2fs

---

### Post by endfx on 2007-11-18
Thanks for the information.

atlfalcons866: Can I ask why you think XFS corrupts easily? Do you have any references for this or is this from personal experience? I'm just curious because I can only find good things about XFS.

Thanks for the help.

---

### Post by atlfalcons866 on 2007-11-18
[http://en.wikipedia.org/wiki/XFS#Disadvantages](http://en.wikipedia.org/wiki/XFS#Disadvantages)
XFS delays allocation and ordering of meta-data and data flush to disk. XFS may choose not to write data to the disk when it is received, so loss of data during crash is more likely.

reiserfs is a joke.

THe only file systems that i find solid are JFS ext3 (same goes to ext2 because ext3 is ext2 with just journaling).

Ive used XFS before my power went out and the whole fs got corrupted.

---

### Post by atlfalcons866 on 2007-11-18
[http://en.wikipedia.org/wiki/ReiserFS#Criticism](http://en.wikipedia.org/wiki/ReiserFS#Criticism)
Criticism

Some directory operations (including unlink(2)) are not synchronous on ReiserFS, which can result in data corruption with applications relying heavily on file-based locks (such as mail transfer agents qmail[4] and Postfix[5]) if the machine halts before it has synchronized the disk.[6]

There are no programs to specifically defragment a ReiserFS file system, although tools have been written to automatically copy the contents of fragmented files hoping that more contiguous blocks of free space can be found. However, Reiser4 will have a repacker that optimizes file fragmentation.[7]

[edit] fsck

The tree rebuild process of ReiserFS's fsck has attracted much criticism: If the file system becomes so badly corrupt that its internal tree is unusable, performing a tree rebuild operation may further corrupt existing files or introduce new entries with unexpected contents [8]. But this action is not part of normal operation or a normal file system check and has to be explicitly initiated and confirmed by the administrator.

Nevertheless it is recommended not to store ReiserFS v3 images on a ReiserFS v3 partition (e.g. backups or disk images for emulators) without transforming them to a form that avoids misleading the file system, e.g., by compressing or encrypting. Reformatting an existing ReiserFS v3 partition can also leave behind data that could confuse the rebuild operation and make files from the old system reappear. This also allows malicious users to intentionally store files that will confuse the rebuilder. As the metadata is always in a consistent state after a file system check, corruption here means that contents of files are merged in unexpected ways with the contained file system's metadata. The ReiserFS successor, Reiser4, fixes this problem.

[edit] Earlier issues

ReiserFS in versions of the Linux kernel before 2.4.16 were considered unstable by Namesys and not recommended for production use, especially in conjunction with NFS.[9]

Early implementations of ReiserFS (prior to that in Linux 2.6.2) were also susceptible to out-of-order write hazards. For example, files being appended to during a crash gained a tail of garbage upon next mount.[citation needed] But the current journaling implementation in ReiserFS is now on par with that of ext3's "ordered" journaling level.

---

### Post by Giradman on 2007-11-18
> **endfx said:**
> 
Every so often I have to reboot a server and sometimes I get a message similar to:
"filesystemX has gone Y days without being checked. Check forced"

And then does a full filesystem scan.....................


New to Ubuntu on an old IBM laptop - I've been shutting down daily and re-booting; after about 30+ reboots, the above occurred - I assumed that this was a 'normal event' but was not sure - seems from the discussion that this is to be expected? Will follow this thread closely to determine if I may want to change the defaults?  Or, is it a good idea to have this disk checked runned periodically (and this often)? - still learning about this OS - thanks all - :)

---

### Post by atlfalcons866 on 2007-11-18
it is always good to check the file system periodically. when i was using jfs it never fscked itself on me.

---

### Post by avik on 2007-11-18
The same thing happened to me again, and it was just then that I found this thread.  :lolflag:

But, once again, while it may be annoying if you have a large hard drive, it's still a good idea to have you hard drive checked every once in a while.

---

### Post by atlfalcons866 on 2007-11-18
the problem with ext3s fsck it checks every single Inode even ones that arnt used which makes it a HUGE problem with large harddisks. I hear of people with 2 Terabyte hard disks that they had to wait a week for it to be done. I found JFS fsck a lot faster.

---

### Post by atlfalcons866 on 2007-11-18
ext4s fsck is suppose to fix this problem

---

### Post by fjgaude on 2007-11-18
> **atlfalcons866 said:**
> the problem with ext3s fsck it checks every single Inode even ones that arnt used which makes it a HUGE problem with large harddisks. I hear of people with 2 Terabyte hard disks that they had to wait a week for it to be done. I found JFS fsck a lot faster.

I have 500 and 300 GB drives and they get checked in about a minute or less, usually. I wonder why the really long time? Does it mean that fsck has lots of work to do when it takes that long? It finds things it has to do to the filesystem to get it back into being 100%?

---

### Post by atlfalcons866 on 2007-11-18
what file system do you use?

---

### Post by fjgaude on 2007-11-18
I use only ext3 for software raid and for boot disk.

---

### Post by atlfalcons866 on 2007-11-18
maybe because its the amount of files then. i have 200000 files on my / and that takes 2 mintues and that is only 12Gb. My /home is 133Gb and only has 13k files and it takes 4 minutes.

---

### Post by fjgaude on 2007-11-18
Fast RAM and CPUs could have a speedup effect, maybe?

---

### Post by atlfalcons866 on 2007-11-18
yes they do!

---

### Post by fjgaude on 2007-11-18
Also the latest perpendicular read/write drives are really fast compared to the older technology, like 134 MB/sec seq read. Many of the older drives, even the Raptors, were not much over 40 MB/sec.

---

