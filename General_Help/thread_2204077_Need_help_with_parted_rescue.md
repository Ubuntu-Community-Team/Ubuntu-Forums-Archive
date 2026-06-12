---
title: "Need help with parted rescue"
date: 2014-02-06
forum: General Help
---

### Post by dmitry10 on 2014-02-06
My HDD had 4  partitions :
1 NTFS Vista
2 FAT32 - empty, 
3 Ubuntu 8.04 ext3 
4 swap

50GB each, except swap 1.5GB

I tried "expert" installing GoAutoDial 3, but aborted install after seeing that there is no option to install on partition 2
However GoAutoDial 3 took initiative to wipe out partitions, MBR and all. Now computer gives message GRUB Error 22 on boot

Booting with Live CD, parted lists volume as unallocated - all of it.
after reading 3% of disk, rescue found only 3 partitions:
ext3 primary at 585kb -> 107MB
ext3 primary at 737kb -> 108MB
ntfs primary at 1049kb ->: 52.4Gb

Question: What does it mean?Why NTFS is 52 GB, as it should be, and ext3 are 107 mb? They should be 50GB each

I did NOT  "rescue " any of them yet

Thanks!

---

### Post by oldfred on 2014-02-06
grub error 22 is from grub legacy. Not many remember that any more.

Best to use newest version of live installer, so you have latest versions.
I would try testdisk. If you know exact starts and sizes part rescue should work.
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 [https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)


[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

      
 Use parted rescue to restore missing partition details in post #21 & 22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

---

### Post by dmitry10 on 2014-02-06
Thks for your 2 bits oldfred, and for a lot of threads
I will read them some day.

I hope you will read my question too.

If not, maybe you know someone who could explain why RESCUE shows one partition  at correct size, ignores another, and 2 others are listed at a wrong size?
That was my original question.
Maybe someone knows if it is OK to rescue just that one partition , or full recovery is the only way.

Thanks again

---

### Post by oldfred on 2014-02-07
I would still try testdisk if rescue is not showing correct partitions.
Testdisk is usually very good at finding old partitions.

---

