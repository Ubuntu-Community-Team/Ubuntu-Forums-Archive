---
title: "Recovering files from unallocated space using Testdisk and an Ubuntu Live CD"
date: 2012-11-05
forum: General Help
---

### Post by ac3raven on 2012-11-05
So I'm about to replace a failing hard drive, but before I do, I need to get all the files off of its windows partition. The problem in doing that is that the windows partition is no longer formatted as an NTFS filesystem, but is now just unallocated.

I was able to mount the drive with an Ubuntu live cd, and use testdisk to find the files (which are all still intact by the looks of it).

What I need to figure out is how to use testdisk to copy the files from the drive onto another hard drive or flash drive. I know how to copy, but I don't know how to change the destination folder to another disk. Because I can't very well copy >4gb of data into memory (I'm in a live cd environment).

Or, if there is another/better free program to use to view and copy data from unallocated space, I'd like to know about it.

---

### Post by thnewguy on 2012-11-05
If I remember correctly TestDisk saves recovered files into a sub-folder of your current working directory. Which means you should be able to simply mount a remote share, "cd" into that mount point and then run TestDisk on the unallocated partition.

---

