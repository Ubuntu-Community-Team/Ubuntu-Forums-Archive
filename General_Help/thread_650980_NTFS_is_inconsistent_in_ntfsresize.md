---
title: "NTFS is inconsistent in ntfsresize"
date: 2007-12-27
forum: General Help
---

### Post by JamesBowen on 2007-12-27
> 
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 188786622976 bytes (188787 MB)
Current device size: 188786626560 bytes (188787 MB)
New volume size    : 176640 bytes (1 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Cluster accounting failed at 814088 (0xc6c08): missing cluster in $Bitmap
Cluster accounting failed at 814089 (0xc6c09): missing cluster in $Bitmap
Cluster accounting failed at 814090 (0xc6c0a): missing cluster in $Bitmap
Cluster accounting failed at 814091 (0xc6c0b): missing cluster in $Bitmap
Cluster accounting failed at 814092 (0xc6c0c): missing cluster in $Bitmap
Cluster accounting failed at 814093 (0xc6c0d): missing cluster in $Bitmap
Cluster accounting failed at 814094 (0xc6c0e): missing cluster in $Bitmap
Cluster accounting failed at 814095 (0xc6c0f): missing cluster in $Bitmap
Cluster accounting failed at 814096 (0xc6c10): missing cluster in $Bitmap
Cluster accounting failed at 814097 (0xc6c11): missing cluster in $Bitmap
Filesystem check failed! Totally 3848112 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.


I get the above message when trying to resize my ntfs partition.  I am currently running exclusively linux; I have no access to windows whatsoever.  My drive was fine, but then I ran ntfsresize -s 180500M /dev/sda2, which gave me an error similar to this:
> 

ERROR: Extended record needed (1064 > 1024), not yet supported!

Now none of the utilities work, and evidently something is wrong with my ntfs partition.  Is there a linux equivalent to chkdsk I can use to clear up this problem?  I have about 180 gigs of data on this partition.  Most of it is non-critical, but there are a few assignments, projects, etc, I need to recover, so any help you can offer would be most welcome.

---

