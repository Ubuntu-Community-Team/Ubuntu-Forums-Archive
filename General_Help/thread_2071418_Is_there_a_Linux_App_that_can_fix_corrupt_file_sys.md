---
title: "Is there a Linux App that can fix corrupt file system"
date: 2012-10-15
forum: General Help
---

### Post by Stonerz on 2012-10-15
Hi,

I am wondering if there is a Linux application that can fix a file corruption issue I have. It is a FAT system on an SD card that I use in my digital camera. 

The directory structure is still intact but when I try to enter into a directory with files through dolphin or thunar etc I get an input/output error.

If I navigate to the directory in terminal and run ls I get loads of lines with similar message

ls: cannot access /2M^i»L.&#9600;m!: No such file or directory

I have tried running testdisk on it and also ddrescue but I cannot resolve the issue. Has anyone come across this before and is there a way to fix it?

---

### Post by oldfred on 2012-10-15
Part of testdisk is photorec. It scans device for files and tries to recover anything that looks like a file. It only recovers file with extension, but photos have data inside them you can use for renaming.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Karlchen on 2012-10-15
Hello, Stonerz.

The commandline version of the application to fix corrupt filesystems is named **fsck**. Run **man fsck** to get the fsck help pages.

You may also use the GUI programme **GParted**. Inside the **Partition** menu there is an action item labelled **Check** or **Verify** (Sorry, I'm translating back from German to English.).

As we are talking about an SD card: No SD card will live forever. Is it imaginable that the problem is not the damaged filesystem as such, but that the SD card is getting closer to the end of its lifetime?

Kind regards,
Karl

---

### Post by Stonerz on 2012-10-15
photorec recovered the files. I created an image of the SD card using testdisk and then recovered the image to another SD card just in case the original was damaged. Then I ran photorec on the recovered image. Looks like all the files are recovered

---

