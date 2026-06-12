---
title: "Fsck deleted entire folders on HDD"
date: 2013-12-13
forum: General Help
---

### Post by Xan63 on 2013-12-13
Hi all!

I have an external harddrive (WD) of 2 To, formatted in Fat32 and had frequently the error "Input/Output issue" while trying to copy a bunch of videos.

After unmounting my harddrive, I tried to ran Fsck, which asked me the following:

> sudo fsck /dev/sdc1
fsck de util-linux 2.20.1
dosfsck 3.0.16, 01 Mar 2013, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:44/20, 72:49/20, 73:53/20, 74:4b/20, 75:41/20, 76:54/20, 77:4f/20
  , 78:54/20, 79:4f/20, 80:00/20, 81:00/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
/Sauvegarde
 Start does point to root directory. Deleting dir. 
/ToToYo/Jeux
 Start does point to root directory. Deleting dir. 
/ToToYo/MP3
 Start does point to root directory. Deleting dir. 
/ToToYo/Sauvegarde
 Start does point to root directory. Deleting dir. 


When I saw that it was starting to delete these directories, I immediatly stopped the process with CTrl+C.

After googling a bit to see how to recover these files, I tried testdisk - but it does not show the files as "Deleted".

Do you have any idea/advice of what I could do to recover these files - and solve this "Input/Output" issue? Recovering the files is the most important issue now... i'm a bit desperate to find them back!:(

Thanks a lot for your help!

---

### Post by oldfred on 2013-12-13
Is there a lost & found folder or have you looked in Deleted files in you system? Not sure how Linux dosfsck works.

But a 2TB FAT32 is asking for issues. Better to use NTFS if you want Windows compatibility. 
FAT32 cannot store any files over 4GB, so if any of your movies were larger that may be the reason for the errors.
Also FAT32 does not have a journal, so recovery is more difficult.

You may then have to use photorec. But that can be a very slow process as it just scans drive for anything that looks like a file. Photorec is part of testdisk.

---

### Post by Xan63 on 2013-12-15
Hi oldfred,
thanks a lot for your help!

I've checked the Lost+Found file  of the system (using gksudo nautilus - don't know if that's the best way to do) and there's unfortunately nothing in it. In the harddrive repositories, there is no Lost+Lost file.

Thanks for the advice regarding Fat32 and NTFS - I indeed wanted to have access to my HDD under Win$. But is NTFS well supported under Linux? I've read here and there the driver might not be fully supported. Is there any other HDD format supported both by Linux and Windows?

I'm going to test photorec - keep you posted! thanks!

---

### Post by oldfred on 2013-12-15
In 2006, I read info that NTFS was not yet well supported, so I did use a FAT32 for my shared with XP partition. But in 2009, I converted to 64 bit, and a new hard drive, so I also converted my shared FAT32 to NTFS. Had no issues.

Often the issue now is that the Linux NTFS driver shows all files & folders. I used to turn that on in Windows and regularly corrupted Windows. So I often suggest to set a Windows system partition as read only but use a data partition as read/write. 
Also hibernation in Windows will cause issues. It saves old file structure and restores that. Then any file or folder added from Ubuntu is not seen.

Photorec and similar tools require a lot of effort. I used photorec to restore some missing text files. I had saved them many times since last backup and photorec found every copy. But since it does not find filenames, I had to sort txt files and do a lot of compares to see if I could tell which was the most recent. Photos & music have internal meta data that can help to restore names.

Some suggest this for NTFS, I think it has a FAT version. Sometimes Windows tools may work better for Windows.
       For NTFS 
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)

---

### Post by Xan63 on 2013-12-16
As I don't have a dual boot with Windows, but only use my HDD time to time with others Windows pc - would this kind of use corrupt the Windows of others pc's?

I've tried Photorec- but didn't chose the type of file and finally ran out of free space on my laptop... I'm gonna run it again - and this time, with the good format file chosen!

Thanks again for the tips!

---

### Post by oldfred on 2013-12-16
Because it also recovers deleted data (does not know difference), it can take a lot of file space for recovery. You can set it to only find certain file extensions, but it does not make it faster as it still is doing a low level scan of drive. And it will recovery some partial files that are not correct.

Ubuntu runs fsck on the Linux partitions every 40 or 60 reboots. I do not think Windows runs chkdsk automatically except on error on booting. And if a data drive, chkdsk may never get run. Best to run it from Windows on a regular cycle. You cannot run chkdsk from Linux.

More info on photorec.
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
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

