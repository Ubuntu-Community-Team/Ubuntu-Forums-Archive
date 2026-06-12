---
title: "Ext4 was formated to ext2. How to recover data?"
date: 2013-08-21
forum: General Help
---

### Post by xLukas on 2013-08-21
I was updating my sisters laptop (by doing clean install). It should have to reformat / partition + mount /home to new OS.

But for some reason it ended up with my old ext3 /home 400gb partition to be formatted to ext2. I have no idea how this could have happened, not it matters now.
In theory reformat should just destroyed my original partition table, but files should be intact (or at least I hope so).

At the moment I have HDD removed from laptop and installed into external USB case. 

First question - how likely is it to recover deleted files, and how likely to do so including file names?

Second question - where to start?

thank you for any help

---

### Post by oldfred on 2013-08-21
I would start with testdisk and do the deeper search. That probably is the only way you will get file names. 

If you have to use photorec, you only get extensions and have to manually rename files. Photos & music have internal meta-data that will allow renaming but everything else you have to manually rename.

Testdisk is in the Ubuntu repository and on many Linux repairCDs.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[URL="http://www.cgsecurity.org/wiki/Menu_Analyse"]http://www.cgsecurity.org/wiki/Menu_Analyse

[/URL]
 [http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]https://help.ubuntu.com/community/DataRecovery#Lost%20Partition


[/URL]

[URL="http://www.cgsecurity.org/wiki/Menu_Analyse"]
[/URL]

---

### Post by xLukas on 2013-08-22
Thanks, for sure I'll try this.

At the moment I had this HDD attached to laptop with w8 and started Easy Recovery. Surprisingly with 75% scanned it shows that 100k files 5k folders have been found. sadly until it finishes I cant see if files were saved.

At the same time I started R-Linux, it found some files, but video files were not complete and had random names. But since I stopped it after like 1% - I hope it would be able to recover better (2 recovery tools at the same time is a torture to laptops hdd)

---

