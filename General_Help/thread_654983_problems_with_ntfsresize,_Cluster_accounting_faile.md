---
title: "problems with ntfsresize, Cluster accounting failed at 135593 (0x211a9): missing clus"
date: 2007-12-31
forum: General Help
---

### Post by go_beep_yourself on 2007-12-31
I believe the ntfs-3g driver in Linux has destroyed Windows on my other hard drive. After saving a file using gimp to Windows, I could not delete or view that file from Windows. Even though an icon was showing on the Windows desktop for that picture that Gimp had put there, double clicking it created a message saying that the file did not exist. I was able to delete the file from Linux, but now each time I use Windows, it crashes within 15 minutes. It seems to be crashing sooner now. It's not doing a blue screen of death. It's not giving any error messages. All it is doing is after using it for a little amount of time, it will freeze for about 2 seconds, and then my screen goes black, and my computer reboots. I've done several disk checks when Windows is starting and even ran ntfsfix on the Windows prtition from within Linux several times. I did a "check and repair" using gparted, and this is the message I got.

```
GParted 0.3.3

 Libparted 1.7.1

 
Check and repair filesystem (ntfs) on /dev/sdb1  00:02    ( ERROR ) 
      
   calibrate /dev/sdb1  00:00    ( SUCCES ) 
      
  path: /dev/sdb1
start: 63
end: 138110804
size: 138110742 (65.86 GiB) 
   check filesystem on /dev/sdb1 for errors and (if possible) fix them  00:02    ( ERROR ) 
      
  ntfsresize -P -i -f -v /dev/sdb1 
      
  ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 70712697344 bytes (70713 MB)
Current device size: 70712699904 bytes (70713 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 135593 (0x211a9): missing cluster in $Bitmap
Cluster accounting failed at 135594 (0x211aa): missing cluster in $Bitmap
Cluster accounting failed at 135595 (0x211ab): missing cluster in $Bitmap
Cluster accounting failed at 135596 (0x211ac): missing cluster in $Bitmap
Cluster accounting failed at 135597 (0x211ad): missing cluster in $Bitmap
Cluster accounting failed at 135598 (0x211ae): missing cluster in $Bitmap
Cluster accounting failed at 135599 (0x211af): missing cluster in $Bitmap
Cluster accounting failed at 135600 (0x211b0): missing cluster in $Bitmap
Cluster accounting failed at 135601 (0x211b1): missing cluster in $Bitmap
Cluster accounting failed at 135602 (0x211b2): missing cluster in $Bitmap
Cluster accounting failed at 135603 (0x211b3): missing cluster in $Bitmap
Cluster accounting failed at 135604 (0x211b4): missing cluster in $Bitmap
Cluster accounting failed at 141946 (0x22a7a): extra cluster in $Bitmap
Cluster accounting failed at 141947 (0x22a7b): extra cluster in $Bitmap
Cluster accounting failed at 141948 (0x22a7c): extra cluster in $Bitmap
Cluster accounting failed at 141949 (0x22a7d): extra cluster in $Bitmap
Cluster accounting failed at 141950 (0x22a7e): extra cluster in $Bitmap
Cluster accounting failed at 141951 (0x22a7f): extra cluster in $Bitmap
Cluster accounting failed at 141952 (0x22a80): extra cluster in $Bitmap
Cluster accounting failed at 141953 (0x22a81): extra cluster in $Bitmap
Cluster accounting failed at 141954 (0x22a82): extra cluster in $Bitmap
Cluster accounting failed at 141955 (0x22a83): extra cluster in $Bitmap
Cluster accounting failed at 141956 (0x22a84): extra cluster in $Bitmap
Cluster accounting failed at 141957 (0x22a85): extra cluster in $Bitmap
Cluster accounting failed at 5912473 (0x5a3799): extra cluster in $Bitmap
Cluster accounting failed at 5912474 (0x5a379a): extra cluster in $Bitmap
Cluster accounting failed at 5912475 (0x5a379b): extra cluster in $Bitmap
Cluster accounting failed at 5912476 (0x5a379c): extra cluster in $Bitmap
Cluster accounting failed at 5921646 (0x5a5b6e): extra cluster in $Bitmap
Cluster accounting failed at 5921647 (0x5a5b6f): extra cluster in $Bitmap
Cluster accounting failed at 5921648 (0x5a5b70): extra cluster in $Bitmap
Cluster accounting failed at 5921649 (0x5a5b71): extra cluster in $Bitmap
Filesystem check failed! Totally 32 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
 

  ========================================

 
Check and repair filesystem (ntfs) on /dev/sdb2 

  ========================================

 
Check and repair filesystem (ext3) on /dev/sdb3 

  ========================================
```

If I boot to Windows and open a command prompt and type chkdsk /f. It says that is not allowed because the volume is in use. Is that any different than the chkdsk that runs before logging into Windows?

---

