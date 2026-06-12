---
title: "Help restoring partition"
date: 2015-11-15
forum: General Help
---

### Post by sandro12 on 2015-11-15
toady i had some stuggle installing ubuntu on new ssd and after finally booting up ubuntu i found that my old windows ntfs partitions on hdd was deleted. I suddenly without knowing that i was doing a bad thing, made an new ntfs partition. 
after that i started searching for recovery of partition and found out i did a very bad thing that i made new ntfs on top of old. 
Is there any way for recoverying partion which was overwritten by new partition?
testdisk find a new made one so please help me :( :(

---

### Post by oldfred on 2015-11-15
Does testdisk show old partition also. Usually it finds all the old versions of partition table and you have to select the correct combination of partitions.
Drilling down may show files which you then could backup.

If not you may be able to use photorec, but often Windows third party tools may work for NTFS better.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

        [https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu](https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu)
Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS
      [/URL]
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.


 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

 
    [URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

---

