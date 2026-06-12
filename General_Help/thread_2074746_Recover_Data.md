---
title: "Recover Data"
date: 2012-10-22
forum: General Help
---

### Post by bazbeata on 2012-10-22
Hi - I was having major issues with Ubuntu last week (I think NVidia driver issues) whereby I just could not login to my pc. I ended up re-installing Ubuntu as a result, but even this was not solving the issue. Every time I re-installed after a couple of restarts, the same hanging on boot up was occurring. 

Then, after a long day of the above (in my defence) I went and did a re-install onto my external hard-drive, which had almost 5 years of documents/images/music/emails backed up on to it :-( 

Once I realised my error I found a notice to try TestDisk to identify the deleted files and recover them, but to no avail!

I've spoken to a data recovery company who recommend taking an image of the external hard drive and purchasing software called r-studio. I am a complete layman when it comes to things like this (as the above shows) - any help would be gratefully received.

---

### Post by raja.genupula on 2012-10-22
To know more information you must read this 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by bazbeata on 2012-10-22
Thanks Raja - I was hoping I could get a more step by step guide. I've installed gddrescue but not sure what to enter in the [] where it says "Run gnuddrescue like this: ddrescue [options] infile outfile [logfile]" also the file name/location (I have attached a screenshot of the properties of the extrenal hard drive I have lost the data from). Any help is gratefully received.

---

### Post by oldfred on 2012-10-22
Data may be anywhere on drive depending on how you had it partitioned. You screenshot is only showing after the new install.

dd is an exact bit for bit copy, so you have to have another 500GB drive to copy image to. Will take a long time but if working on drive erases more data then there is no other way to recover it.

I have used photorec. Most data is not erased, but if you reinstalled some have been overwritten. Photorec just scans entire hard drive for anything that looks like a file. It does not recover full file name but will recover extension based on what file looks like on drive. It also needs lots of room as anything that looks like a file is copied to your new location.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

When I used photorec, I think it took 6 hours to scan my drive. I had text files that I had not backed up for a while and then saved almost every day. It found every copy since my drive had lots of room. Never was sure I found last saved copy but had to do a lot of file compares and searching thru files to find the right ones. Took a long time. Or now I do more frequent backups. :)
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by olivias38 on 2012-10-23
There are chances that a lot of data is overwritten now. You can still recover the data which is not overwritten yet. You can try Kernel for Linux utility for recovering data.

---

### Post by Mark Phelps on 2012-10-23
Unless you formatted the external drive yourself, it's likely it was formatted with a Windows filesdystem -- NTFS or FAT.  If that's the case, using Linux utilities to recover the data will have little success.  You need to let us know the format of the partitions so we can advise you what will work best.

---

