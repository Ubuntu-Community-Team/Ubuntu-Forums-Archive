---
title: "Directory deleted but file still available - is it still using disk space?"
date: 2020-03-29
forum: General Help
---

### Post by thombark2 on 2020-03-29
Hello,  I am using 18.04 MATE. I accidentally deleted a directory while using VLC to view a file in that directory. Because I was viewing the file, it must have stopped the file from being deleted because I was able to view the whole file which was very large. However during this viewing the directory was not visible.  Could the file's disk space still be reserved? The disk is EXT4 and the partition is Linux Bootabe.  Thank you.

---

### Post by ajgreeny on 2020-03-29
I suspect the file in that deleted directory was in RAM after being played but I fear that it will probably no longer exist once you shutdown VLC or reboot.

It may be possible to play the file again in VLC and use VLC's option to record what's being played.  To see the record button you may need to go to **View ->Advanced Controls** in the VLC menu.

---

### Post by Holger_Gehrke on 2020-03-29
Yes, the file still exist as long as some program has it open. Deleting a file from an ext4 file system removes the name, but the inode doesn't get marked as free and the blocks aren't moved to the free block list until the file is not in use by any program any more. It's actually a well known technique to create a temporary file, open it for reading and writing, delete it and keep right on using the file through the file handle given to you during opening the file - that way nobody can easily snoop in your temporary data (it's not impossible,but it's a lot harder) and the clean-up when shutting down the program gets simpler.

Holger

---

### Post by TheFu on 2020-03-29
if a program is still using the file, then the inode is still available in the /proc/{PiD}/FD directory.  When we remove a file, the index for that file in the directory "file" removes it.  Until the last process closes the file, the file system doesn't actually delete the inode.  
Take a look under /proc. it is a pseudo-file system.
This was how people used to get perfect copies of streamed videos that had weenie DRM 15 yrs ago.  Just grab the FD out of /proc/ for the video.  DRM has come a long way since then and it also explains why Linux support wasn't on anyone's effort list since pretty much any DRM can be broken that doesn't mandate closed hardware solutions.

File systems are really cool.

But having daily, automatic, versioned, backups are still the best solution to almost every file system issue AND most security issues as well.

---

