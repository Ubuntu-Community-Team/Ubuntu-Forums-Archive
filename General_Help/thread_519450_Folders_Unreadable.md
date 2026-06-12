---
title: "Folders Unreadable"
date: 2007-08-07
forum: General Help
---

### Post by johnb820 on 2007-08-07
Ok well, I was in the process of resizing my main partition to create a new partition and in the middle of this process the power went out here for a whole two seconds. :mad:  Anyway, as you can imagine this has pretty much screwed up the original partition.  The problem I seem to be having is that many of the directories under / are not really directories any more.  Under properties they are of an unknown type with no information on them and they appear as files in nautilus.  The only four directories I have right now are dev, lost+found, mnt, and opt.  I really don't know what direction I should head toward in order to fix this or if there is even a way to recover my system.  After searching around for many, many hours I have yet to really come across anyone that this has happened to.  Any help would be much appreciated.

---

### Post by dfreer on 2007-08-07
Well, I'm guessing your files are corrupted due to the power failure. But just in case, try checking the permissions on those folders. They need to be at least 755 (executable), otherwise you will be able to see them but not navigate into them. Just a thought, maybe the file permissions got hosed up.

---

### Post by distroman on 2007-08-07
If it is file permission issue I was ones able to fix it on a reiserfs file system with fsck.

[http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html)
[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)

---

### Post by johnb820 on 2007-08-07
Thanks for the ideas.  I checked the permissions of the folders and it came back with an input/output error.  When I ran fsck on the drive it found no errors and said the drive was clean.  I know that all of my data is there but there is no way to access it because it doesn't recognize the directories.  I know it sounds like I am pretty much toast, but is there any other way around this?

---

### Post by johnb820 on 2007-08-07
In case anyone else has some thoughts on this I found a post  here 
[https://lists.dulug.duke.edu/pipermail/dulug/2007-April/010842.html](https://lists.dulug.duke.edu/pipermail/dulug/2007-April/010842.html) 
that seems to indicate that the inodes are unreadable.

---

### Post by dfreer on 2007-08-07
I remember hearing about this in another thread where the OP had lost data, evidently this software helped him/her recovery their data:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
I've never used it myself. Just had the link saved ;)

---

### Post by johnb820 on 2007-08-07
Thanks defreer.  I'll look into that.

---

