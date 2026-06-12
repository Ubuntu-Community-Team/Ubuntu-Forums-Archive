---
title: "Problem with the hard drive and lost data!!!"
date: 2013-03-18
forum: General Help
---

### Post by thexnightmare on 2013-03-18
Dear all,
I have:
- windows 7 and on hdd0 (SSD 120GB 1 partition).
- ubuntu on hdd1 (SSD 120GB 1 partition).
- Movies, Softs and Datas on hdd2 (3TB 1 partition).
My son was using the PC, and he restart it, and once restarted, the hard drive (hdd2) was not found, he goes to computer disk management on windows 7, and the system ask him to choose MBR or GPT partition stye and the disk showed as unallocated. The hard disk originally was GPT, but my son click on MBR, then he reallocated the disk and create new volume, and therefore, the disk is now empty!!!
I didnt touched the disk since then, and donno what to do, and I am sure that the problem is not from my son, but from the stupid windows OS.
In all cases, any help with restoring the data from the hard drive?
Thanks in advanced

---

### Post by carl4926 on 2013-03-18
There are tools that **may **help, such as TestDisk
Not my speciality so wait around

---

### Post by zero2xiii on 2013-03-18
Hay,

 Yep +1 for testdisk. Use google. There is a very complete wiki on recovering lost or deleted partitions.

If you fail after following the wiki, ask here again for further assistance.

Regards :)

---

### Post by varunendra on 2013-03-18
+1 to testdisk.

Follow [this guide]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") to search for lost partitions. If found after "deeper search", ensure the existence of files using 'P' option as mentioned in the guide. You can then either copy the files in the same screen, or 'Write' the partition layout to the partition table to get them back.

Be sure NOT TO DO ANYTHING THAT WRITES on the data area of the disk until all the data is recovered and verified.

---

### Post by tgalati4 on 2013-03-18
Windows is very friendly:  "Volume not recognized.  Would you like to format it?"  Not linux friendly at all.

Wait until he asks to borrow the car.

Here's some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Do lots of reading first before attempting recovery, so you understand what is going on.  Don't just blindly follow the first tutorial that you find.  The data is not going anywhere--unlike your sanity.

---

### Post by oldfred on 2013-03-18
+1 on testdisk
You are not the first to post with major issues from Windows and 3TB drives.

But you may also want to see what gdisk or sgdisk say about drive. Because gpt has a backup partition table at the end of the drive and MBR partitioning cannot go beyond 2TB, the backup may still be valid. But not sure what it will say nor if data files inside partition will still be seen. 

[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
>  Overwritten GPT main header or table&#8212;Various disk utilities have been written to store data in the unused (on true MBR disks) area between the MBR and the start of the first partition. Such utilities, if run on a GPT disk, might overwrite some or all of the GPT main header or partition table. You can use the 'b' and 'c' options on gdisk's experts' menu to have the program use the backup header and partition table, respectively, thus recovering from this problem. 



---

