---
title: "Recovery directory from NTFS partition"
date: 2013-11-27
forum: General Help
---

### Post by jaro.zelenak on 2013-11-27
Hello, 
I'm desperate, I accidentally deleted all partitions on my laptop, while installing lubuntu, then, fortunately I recovered the important NTFS partition, but to my surprise It recovered everything, movies, mp3s and other stuff but not the MOST IMPORTANT directory, with my dokuments, photos, works. It looks according to free space on a disk, that everything was recovered, but there is nothing in that directory and when I try to list directory it says: ls: reading directory .: Input/output errors: reading directory .: Input/output error.
Thank you in advance for your answer.

---

### Post by Sef on 2013-11-28
Take a look at [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

From the Photorec site:

> [PhotoRec]("http://www.cgsecurity.org/")[COLOR=#000000][FONT=sans-serif] is file data recovery software designed to recover lost files including video, documents and archives from hard disks, CD-ROMs, and lost pictures (thus the Photo Recovery name) from digital camera memory. PhotoRec ignores the file system and goes after the underlying data, so it will still work even if your media's file system has been severely damaged or reformatted.[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]PhotoRec is free - this open source multi-platform application is distributed under [GNU General Public License]("http://www.gnu.org/copyleft/gpl.html") (GPLV v2+). PhotoRec is a companion program to [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), an application for recovering lost partitions on a wide variety of file systems and making non-bootable disks bootable again. You can download them from this [link]("http://www.cgsecurity.org/wiki/TestDisk_Download").[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]For more safety, PhotoRec uses read-only access to handle the drive or memory card you are about to recover lost data from. Important: As soon as a picture or file is accidentally deleted, or you discover any missing, do NOT save any more pictures or files to that memory device or hard disk drive; otherwise you may overwrite your lost data. This means that while using PhotoRec, you must not choose to write the recovered files to the same partition they were stored on.[/FONT][/COLOR]

---

### Post by Mark Phelps on 2013-11-28
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

