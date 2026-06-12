---
title: "Is possible to convert a data filled RAW FS to FAT or NTFS without losing data?"
date: 2013-04-21
forum: General Help
---

### Post by evets on 2013-04-21
Recently, I was struck by several electrical power outages in a very short period. This was very much akin to turning a light switch off and on in rapid succession. So quickly, in fact, it didn't even trip my power strip or UPS, although the UPS did offer a few quick beeps, and the lights in my house did flicker. ( the clocks on the stove and microwave reset to 00:00, but not the alarm clocks-weird )

I have 2 Ubuntu boxes, a Windows7 box, and several Windows XP boxes.  All of which, excepting the single Win7 box, I was able to get to boot, and now operate fine.  The Win7 box, a Lenovo, appears to have lost the MoBo and the USB drive attached is no longer accessible from ANY Windows OS.  I can access it through my Ubuntu boxes, no problems there. It seems the FS is now RAW, instead of the FAT I had it formatted to. Windows sees a RAW partition and believes it to be unformatted, and asks if you want it to be formatted. 

I know, I know, the simple solution would be to back up that USB drive from an Ubuntu box, reformat it and reload the data back on it.  If only... 

The problem is, is that it contains 465GB of data and I don't have a drive that large. Nor do I have any number of spare drives equating to ~500GB. Sadly, I'm broke, busted and disgusted, so I don't have the where-with-all (money) to buy one, either.   

I was cruising around the -net looking for answers, and found none. I have found several posts, here and there, that led to me to believe that there is a method using Linux to accomplish this. Does anyone here have experience or the knowledge to do this? Will you help me by sharing it? 

I appreciate all offers of help! 


Thanks

---

### Post by oldfred on 2013-04-21
RAW means the NTFS or FAT32 partition boot sector (PBR) are not valid. I know NTFS has a backup that testdisk can restore. Not sure about FAT32. And testdisk can create a new PBR for NTFS.

       repairs including testdisk info & links - Test disk is in repository and on many repairCDs.
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


 As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

See if deeper search also finds files, if so immediately backup from testdisk. If none of that works, part of test disk is photorec. But that can be a long slow process.

---

