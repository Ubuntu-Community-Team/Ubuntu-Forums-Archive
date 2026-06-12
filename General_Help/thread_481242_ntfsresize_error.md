---
title: "ntfsresize error"
date: 2007-06-22
forum: General Help
---

### Post by malfist on 2007-06-22
I'm trying to resize my ntfs partition from Ubuntu because PM is throwing error 117, can't find drive letter and the boot disks for Partition Magic do the same and tell me the disk is all bad and one partition. Currently it has one windows partition in the front (starting at 68) and then some unallocated space which will be used for slackware, ubuntu's partition and swap, and a backup partition storing most of what I need, music etc, it's ntfs.

I want to shrink the windows partition more, leave it will only 1GB of freespace so I have more room to test and play around with slackware and see if it is the distro for me. The tool ntfsresize is throwing an error when I do the test run:
> 
jerome@jerome-desktop:~$ sudo ntfsresize  --force -ns 67637M /dev/hdc1
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/hdc1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 75417555456 bytes (75418 MB)
Current device size: 75417560064 bytes (75418 MB)
New volume size    : 67636994560 bytes (67637 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 66637 MB (88.4%)
Collecting resizing constraints ...
Needed relocations : 1164196 (4769 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1064 > 1024), not yet supported!
Please try to free less space.

I'm using the option '--force' because I have just resized it with GParted and it wasn't updated correctly and told me I had less freespace on the windows partition.

Any ideas how to fix this?

---

