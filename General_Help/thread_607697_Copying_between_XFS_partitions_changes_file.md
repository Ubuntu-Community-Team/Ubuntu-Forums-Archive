---
title: "Copying between XFS partitions changes file"
date: 2007-11-09
forum: General Help
---

### Post by Rob_Quads on 2007-11-09
I am having a problem copying a file from one XFS filesystem to another. I have downloaded an ISO from the web into a drive which has a single XFS partition. I MD5ed the ISO and it all shows it came down fine.
If I copy that file to another directory on the same drive everything is fine but if I copy it to another XFS partition (tried two both part of RAID arrays) then the resulting file has a different MD5SUM.
i.e.

/ = ext3 - Single Disk
/temp = XFS - Single Disk
/Stuff = XFS - LVM RAID
/Video/Other = XFS - LVM RAID

 /temp/Torrents/MyFile.iso - MD5SUM = 83909703a60283ffc8f3da1d8a8594f0

If I copy the file from /temp/Torrents/ to the following directories I get

/home/<user/  MD5SUM = 83909703a60283ffc8f3da1d8a8594f0 (different drive - non LVM RAID)
/temp/MyDir/   MD5SUM = 83909703a60283ffc8f3da1d8a8594f0 (same drive)
/Stuff/             MD5SUM = 4c123d325343a41d021c88eb6ac687c4
/Video/Other   MD5SUM = bf8c4e7818a5eba52dcdff287de4e496


Anyone know what could cause the file to be changing copying it to the other filesystem? I have tried using cp and also mv but if I mv the file it also changes.

---

### Post by mixmaster on 2007-11-09
Dumb questions:
Is the file the same size after copying?
If you copy it off the raid and back is the MD5 checksum restored to its original value, unchanged or changed to some third value?
Does this happen with other (smaller) files?
What sort of RAID (0, 1 , 5, hardware, software)

---

### Post by Rob_Quads on 2007-11-09
File is the same byte size on all directories
Copying the file a second time to the RAID drives result in different MD5s so copying out and back in again I expect will change the file.

I have tried copying another file which is 5.5GB and it copied across fine keeping the same MD5sum so it appears to be something about this file which is very strange.

---

