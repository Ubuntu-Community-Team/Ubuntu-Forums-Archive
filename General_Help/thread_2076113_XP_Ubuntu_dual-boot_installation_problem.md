---
title: "XP Ubuntu dual-boot installation problem"
date: 2012-10-25
forum: General Help
---

### Post by A4Andy on 2012-10-25
I have a machine which runs on dual-boot xp and ubuntu 11.10 after I have a problem with my XP, I decided to reinstall xp. During the installation I deleted my xp partition then created a new one. I also accidentally deleted the boot partition dev/sda1(?). 
 
ofcourse I need to reinstall ubuntu 11.10 but during the installation I couldn't see any partition so I decided not to install ubuntu for the meantime. I access the live mode and for some reason I couldn't access disk utility. I couldn't see my home partition and root partition I would like not to remove the home partition since there were important files there
 
When I went to gparted under partition: unallocated, filesysted: unallocated size 298.09 GB my drive is 320 GB

---

### Post by oldfred on 2012-10-25
Welcome to the forums.

I would from liveCD use testdisk and see if it shows old partitions. Also does gparted only show one partition? 

Did you have a wubi install? if so you deleted Ubuntu when you deleted Windows. Wubi is just a file inside the NTFS partition.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

