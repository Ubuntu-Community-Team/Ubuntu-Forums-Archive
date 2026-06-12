---
title: "Undo mkfs.ext4"
date: 2014-06-22
forum: General Help
---

### Post by TheShanthan on 2014-06-22
So, as a progression from my ubuntu addiction, I was trying to install Archlinux on another hard drive while watching a tutorial video. I got caught up with the tutorial and used theirs harddrive names and not mine. So, I used mkfs.ext4 on the partition in /dev/sda (where I have a lot of important stuff) instead of /dev/sdb (where I want to install the os). Now, the OS (Win 7) that was on the drive doesn't boot up! I am fine without the OS but is there anyway I can retrieve the files and undo this stupid mistake of mine.

There are some really important files on it. Please help.

---

### Post by Gyokuro on 2014-06-22
Hi

I'm sorry for the bad news but this is not possible - maybe some parts of your files with special forensic tools ([http://forensicswiki.org/wiki/Tools:Data_Recovery](http://forensicswiki.org/wiki/Tools:Data_Recovery)) but for average users I think it's somehow a lost game. Always have a backup of your important files. However if there really important data on it keep the disk as it is and there are companies which are able to recovery some files but this will cost you a lot of money ([http://www.krollontrack.com/data-recovery/](http://www.krollontrack.com/data-recovery/)).

---

### Post by oldfred on 2014-06-22
You can try testdisk with its deeper search, if that does not work then photorec (part of testdisk) or some Windows tools that just scan drive for anything that looks like a file.

If testdisk finds old partitions, you may be able to restore system as long as you did not write any data. But best to backup files if found first.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Photorec is a long slow process depending on drive size. It is just scanning drive so it takes forever, overnight for me with a smaller drive. And then it only recovers files with extension not full name. Photos & music have internal data that can be used to create a new name that is more useful.
      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)


 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by TheShanthan on 2014-06-22
While I was waiting for these reply, I actually came across testdisk and photorec too. TestDisk did not help me but photo rec seems to be getting the job done. As I type this, it is populating a folder in my system with files. They are not named accurately or in correct folders but, I do have them. It is going to be a long night while I try to reorganize them.

---

### Post by oldfred on 2014-06-22
I found photorec also recovered the same text files that I wanted many times as I had updated almost daily. My backup was several weeks old and I had to grep and compare many versions to try to find which had more or updated info.

       Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

