---
title: "marking bad sectors on a disk"
date: 2007-07-02
forum: General Help
---

### Post by Pro_D on 2007-07-02
I am wondering how I can have a destructive (writes and reads patterns to disk) test and have the bad spots get marked.  Data currently on the disk (if any) doesn't matter so formating it is just fine.

I don't know if the mkfs (or rather mkfs.vfat) with -c will do destructive testing through badblocks though.  In the end I need fat32 filesystem to work under win32.  Assuming that mkfs doesn't do a destructive (read/write) test how would I go about feeding badblocks output to mkfs?

I suspect the disk has some stuck bits (based on behavior before considering this) in either the on or off state so doing 2 runs with badblocks with a testpattern ULONG_MAX-1 and another with 0 would net me all the badspots... Of course I don't understand how the -c option works, it may do a thourough enough test for all I know.

I have to comment that it's pretty sad how far backwards disk utilities have gone on windows, at least the ones I am familiar with.

[edit]
After doing some more reading and some testing I have figured out the following:
-badblocks without a -t checks 0xaa only.  I would assume that mkfs would call badblocks either without a -t option or with random as the parameter.  This isn't quite good enough. because:
-after doing a badblocks run with 0x0 (or just 0) for the -t as well as a 0xffff I have a different number of bad spots found, looking at the list the bad spots are different in some places.

I think I also have figured out how to pass the badblocks list to mkfs, I just hope that it will allow for duplicate and unsorted entries - list1 appended to list0.  That or I need a tool that I can use from kubuntu 7.04 live disk to create the final file (merge the 2 files without duplicate entries and in order).  I also apparently need to use the right block size in making the lists but I am familiar enough with fat32 I think - at 512 bytes per sector and 8 sectors per cluster I need a blocksize (for badblocks) of 4096.

It would also still be usefull to know if there is a good tool to do this without formating for fat  (even if it is win32, ubuntu preferred), I think I have one for linux native formats...
[/edit]

[edit2]
I did badblocks -w -b 4096 outputted to a file. I did this with all 0s and all 1s for the bits (two sets of files).  I then played around with the 2 files' data with openoffice spreadsheet and found out that the all 0s produced all the same bad spots as the all 1s, but more.  I then used the mkdosfs -l to point it to the list and I get this nice little tidbit:

mkdosfs 2.11 (12 Mar 2005)
Auto-selecting FAT32 for large filesystem
/dev/sdf1 has 255 heads and 63 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 7936046 sectors;
file system has 2 32-bit FATs and 8 sectors per cluster.
FAT size is 7735 sectors, and provides 990068 clusters.
Volume ID is 468a3d81, no volume label.
mkdosfs: Invalid cluster number in mark_FAT_sector: probably bug!

I could have sworn that fat marked bad spots by the cluster, not by the sector...

Just for the heck of it I also tried using the -c on mkdosfs and after it counts off for a while I get a prompt with no filesystem or additional text.  For some reason it counted to 3961568 while it should only be getting 990068, there is a whole 'nother digit over the max cluster count...

Maybe just too sleepy...
[/edit2]

---

