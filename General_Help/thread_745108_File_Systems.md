---
title: "File Systems"
date: 2008-04-04
forum: General Help
---

### Post by punkle on 2008-04-04
Hi,

I'm a relative beginner to Linux and am confused by the File System concept. I hope someone can help:

Does 'File System' refer to the method by which files are written to data storage, or does it refer to the way in which the data storage devices connected to a system are mounted and displayed through an Operating System? Or is it both?

Brian

---

### Post by LaRoza on 2008-04-04
A file system

[http://en.wikipedia.org/wiki/File_system](http://en.wikipedia.org/wiki/File_system)

The default for Ubuntu is EXT3, Windows uses NTFS.

The directory structure (how the directories are set up): [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by punkle on 2008-04-04
Cool Thanks,

Would I be right in saying that a file system like ext3 deals with the hardware that stores the data on one side and the way that the OS displays it on the other?

What I cant get my head around is, if the above is the case, is ext3 also a mediary between the Operating System and the data volume if it is formatted in NTFS for example?

---

### Post by az on 2008-04-04
A file system is a format.  It's a way the data is organized.

The Operating System expects the data on the disk to be organized a certain way.  The way it is organized depends on the file system.  You can only use one file system at a time for a part of a disk.

The kernel does the interacting between the hardware and the data on the disk.

---

