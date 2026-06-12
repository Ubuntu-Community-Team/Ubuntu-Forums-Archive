---
title: "how to recover a Hard Disk?"
date: 2013-08-14
forum: General Help
---

### Post by caiorrs on 2013-08-14
Hi there,

a couple weeks ago my notebook's HD just stopped working. I will explain.

My Desktop has a 1TB HD (where are the documents) and a 250GB (where are the main systems), the partitions of 1TB HD are in RAW, so I donwloaded the hirens boot cd and ultimate boot cd, then I made a Live-usb with the 2 ISOs. To test them I initialized in my own notebook. I opened the testdisk but it freezed, so I shutted down my notebook and restarted with the usb, and the initiate the mini XP, and restarted, but then there was no system to boot (?). I'm now with the voyager live-usb and there is just the system reserved partition(from windows 7) and 297.99G as unnalocated.

is there any way of me getting all data back? or sort of? I was thinking, is it possible to recover the partitions and restore the boot like if anything happened?

notebook HD 320GB - 160GB ubuntu 13.04 - 140GB Windows 7 (it was it)

thanks, sorry about my english =S

---

### Post by papibe on 2013-08-14
Hi caiorrs.

Here are more tools and examples on the subject: [Data Recovery]("https://help.ubuntu.com/community/DataRecovery").

Regards.

---

### Post by caiorrs on 2013-08-14
thanks, I'm reading it =D

---

### Post by oldfred on 2013-08-14
RAW is a Windows partition without a partition boot sector or PBR or damaged PBR.

If the PBR backup is undamaged you should use testdisk to restore the backup. If you moved partitions or made other changes you may need to use testdisk to create a new NTFS boot sector, but I think that is a XP type. You then need to run chkdsk from a Windows 7 repairCD to fix the PBR to be a repaired Windows 7 type.

       repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you have to try to find missing data and cannot recover partition, then photorec may work. Some also suggest Windows tools for NTFS partitions. 
One user posted this:

 Deleted file alternatives this user liked but not free, both NTFS & FAT available.
[http://ubuntuforums.org/showthread.php?t=1339278](http://ubuntuforums.org/showthread.php?t=1339278)
"GetDataBack for FAT" was the most succesful one among the ones that I've tried. Though it couldn't recover folder's names, it recovered all the files' and sub-folders' name. And it's much better than the others did. Thanks!

---

