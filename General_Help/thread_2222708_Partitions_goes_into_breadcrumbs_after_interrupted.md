---
title: "Partitions goes into breadcrumbs after interrupted operation"
date: 2014-05-07
forum: General Help
---

### Post by Mininao on 2014-05-07
Hi guys !
Yesterday i was trying to reduce the size of a partition with gparted and ubuntu (Gnome 13.10) crashed entirely, while gparted was running.
Needless to say that i was worried about my partitions destiny.
So i booted on a kali linux live cd and tried to launch a repair with testdisk. In fact it totally messed up my hard drive :
[IMG]http://image.noelshack.com/fichiers/2014/19/1399498730-scr.png[/IMG]
(there used to be "Data", "Fichiers", Free space, and a logicial partition containing a little swap and around 55go ext4)
Notice the largest partition in the world at the end.

fsck is'nt sucessful either.
Does anyone know how i could restore my partition ? or at least get the folders back for backup ?
thank you a lot, and sorry for the poor english

---

### Post by oldfred on 2014-05-07
Power failure in the middle of a partition change is about worst case.
Part of data is in one place and part in another and it is about impossible to restore the parts.
Humpty-Dumpty has fallen down. :(

Do you know exact partition sizes before, by sector? If you were just reducing size, only the data at end of partition was being moved so rest may be there. But anything that was being moved may not be.

       Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

If parted or testdisk cannot get partitions back, then photorec is the last choice. I have used it and it takes forever. I had to run it overnight on a smaller drive and have another drive of same size as data it may find. It found in my case all the deleted text files also, but does not find file names, just extensions. So I had to do a lot of grep to find file and file compares to try to find most recent and add text back to last backup.

      
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

---

### Post by Mininao on 2014-05-08
Hi,
thanks for your answer, i will try to recover it with parted.
The only problem (with both Gparted and parted), is that i get the following error when trying to print :
[IMG]http://image.noelshack.com/fichiers/2014/19/1399542557-scr.png[/IMG]
Here is the partition before i attempted to resize it :
[IMG]http://image.noelshack.com/fichiers/2014/19/1399543681-picresized-1399543614-cccc.png[/IMG]

You'll notice that i tried to reduce the size of "Fichiers" only.
My ext4 partition went into breadcrumbs only after testdisk messed it up.

---

### Post by oldfred on 2014-05-08
If it is related to partition table fixparts often rebuilds a partition table. It recalculates correct values for entire drive and  extended partition size. But cannot fix size of a partition.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
And in extreme cases you can manually edit the parts.txt file as it is just txt.

      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 


 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

---

