---
title: "Ubuntu partion mising after Windows 7 BOSD"
date: 2013-10-08
forum: General Help
---

### Post by filip-rychnovsky on 2013-10-08
I have Windows 7 & Ubuntu 13.04 dualboot notebook.
I had hardisk with this layout:
Windows Recovery 15 GB | System reserved 100 MB(windows loader) | Main Win Partion(C:/) 270 GB | Extended partion /Ubuntu 180GB| swap 4GB/

but after Win BSOD and auto-repair,
Grub failed with: no such partion GRUB rescue>
Live CD show up this disk layout:
Windows Recovery 15 GB | System reserved 100 MB(windows loader) | Main Win Partion(C:/) 270 GB | Extended partion /180GB of free space| swap 4GB/

Someone who works as system admin (both windows and linux) and who had rescued many hardisks, has been able to recover windows 7 and windows bootlader to MBR.
So now disk layout is:
Windows Recovery 15 GB | System reserved 100 MB(windows loader) | Main Win Partion(C:/) 270 GB | 180GB of free space| swap 4GB

Windows are working fine, but how to recover ext4 and Ubuntu from these 180GB of free space?
But he has also said that on this free space arent any signs of any known linux filesystem and that begin of this space is very wierd.

---

### Post by oldfred on 2013-10-08
There have been several cases where Windows repairs or reinstalls rewrite partition table and leave off the Linux partition in the extended partition. 
Usually testdisk can restore missing partition and if no other data written into that area it even works again. If you know start & size you also can use parted or maybe even gparted also. Testdisk will find all the old partitions if you resized more than once. You have to choose which is the one with the size - start and size that was the missing one.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

