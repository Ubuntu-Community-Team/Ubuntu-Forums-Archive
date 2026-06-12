---
title: "ext4 partition shown as NTFS after deteling another NTFS partion"
date: 2013-09-04
forum: General Help
---

### Post by mdfaisalpapa on 2013-09-04
I am having a ubuntu server dual booting with Windows XP.Two partitions are of NTFS. The size of ext4 partion was 56 GB . As the space was running out in ext4, i tried to delete one partition of NTFS from windows. but the windows deleted the ext4 partition too. I tried testdisk, it recognizes the partition but showing the partition as NTFS. I am unable to mount the partition in the liveCD too as Gparted too shows the partition as NTFS. Kindly help

---

### Post by oldfred on 2013-09-04
Best to only use Windows to shrink existing NTFS partitions. Its partition tools do not work with Linux partitions and often rewrite partition table incorrectly.

Normally testdisk works, but you may need to do a deeper search? And it often shows multiple choices of old partitions and you have to choose the correct combination that does not overlap.

parted also has rescue mode. But you really need to know start and size of partition.
 [http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by mdfaisalpapa on 2013-09-05
Even deeper search does not show the ext4 partition. Is there any data recovery software that can recover files from ext4 as I  am interested only in some specific files

---

### Post by oldfred on 2013-09-05
Deeper search also should have shown files. If not testdisk also has photorec. I have used it, it is slow as it has to low level scan for anything that looks like a file. I needs lots of room as it copies everything to a new drive. And I found if also finds the deleted files. I had saved some text files many times and it found all of them. Since it only finds extensions not file names I had to do a lot of grepping to find which .txt was which and then compares of each to see if I could tell which was newer. I did have backups but they were not as current as they should have been. I do better now.

       [URL="http://www.cgsecurity.org/wiki/PhotoRec"]http://www.cgsecurity.org/wiki/PhotoRec
[/URL]
 [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[URL="http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html"]http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html

      [/URL]
 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

Some other tools.

 gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 
    [URL="http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html"]
[/URL]

[URL="http://www.cgsecurity.org/wiki/PhotoRec"]
[/URL]

---

