---
title: "input/output error ntfs drive"
date: 2012-12-26
forum: General Help
---

### Post by sahra_kavir on 2012-12-26
Hi,

I have ubuntu and windows on my laptop. I have a separate NTFS partition which I use for storing my files. I have been using Ubutu for read/write to the ntfs partition for a long time. 3 days ago I booted the windows and just opened the ntfs partition without writing any files. Once back in Ubuntu, I realized that some of the directories in the ntfs partition are gone! When I ls into the partition I get input/output error for those directories. The directories do not appear in windows also.


I have already made an image on the partition using ddrescue.
I have tested these with no success: testdisk, ntfsundelete, foremost under Ubuntu and chsdsk under windows

I appreciate any help to recover the data

---

### Post by oldfred on 2012-12-26
Deeper search with testdisk would be my first choice, although if you are getting errors did you run chkdsk or maybe your should.

Have you looked to see if chkdsk moved files to \found folders?

---

### Post by sahra_kavir on 2012-12-27
I restored the partition from the image, ran chkdsk again. Like the last time, it detects all index entries for all files, but instead of recovering them, it simply deletes them. So the output of chkdsk is full of 

deleting index entry...

before running chkdsk the partition is about 40G full (but the directory contents can not be displayed), afterwards it is only about 5 gig full.

---

### Post by oldfred on 2012-12-27
Is chkdsk deleting or moving to \found folder?

Before running chkdsk does testdisk see the files? If not then the backup must not be good either.

---

### Post by sahra_kavir on 2012-12-27
chkdsk just deletes the files.

I have managed to discover the lost files with DiskInternals NTFS recovery, However this software is not free for the actual recovery. I wonder if there is another similar software which is free?

---

### Post by oldfred on 2012-12-27
If testdisk did not see the files with its deeper search, I am not sure what else may work. 

Many suggest Windows tools for Windows systems.

---

### Post by sahra_kavir on 2013-01-22
After testing many free recovery softwares, I finally used the software: Active file recovery from Lsoft, bought a personal software and recovered my files with all directory branches in windows
This was the cheapest working software I found

It was actually a headache to loose all files only because of using a drive on both ubuntu and windows, I read somewhere that this is probably because the NTFS version of Ubuntu and Windows differs, and windows has overwritten the index files.

Thank you for all the help

---

### Post by oldfred on 2013-01-22
Glad you found your data.

The only issues I have heard with the NTFS driver with Linux is when you hibernate in Windows and then any files written from Ubuntu are lost. The hibernation restore the old file structure.
Best to not hibernate and to use a separate NTFS data partition. I used a shared NTFS data partition with XP since 2006 without issue.

---

