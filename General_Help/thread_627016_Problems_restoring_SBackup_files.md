---
title: "Problems restoring SBackup files"
date: 2007-11-29
forum: General Help
---

### Post by mysticrider92 on 2007-11-29
First of all, this problem happened on Arch Linux, but I think the information is basically the same...

I recently backed up my Ubuntu to do a re install. I used SBackup 10.4-2 and saved the file to /var/backup. I then moved the file to my desktop, chmodded it (777 or 755, I don't remember), and tarred it so I could put it on another computer just in case the install went wrong. My install was fine, so the backup file was still on my Arch desktop, and now I am trying to restore it.

When I open SBackup Restore, it will not show the backup. I first tried it with the file on my desktop, and it wouldn't see it after I told SBackup to restore from my desktop. I then moved it back into /var/backup using the root user (/var/backup is not viewable by my regular user), and it still is not recognized. I have tried untarring the files.gz, but I always get an error. 

What should I try? I think it is the file permissions on the backup, but what should they be? This backup file contains most of the files that I had on my computer, and I can't get to them (quite ironic...).

---

### Post by mysticrider92 on 2007-11-29
I took another look at the file I am trying to decompress, and I think there is something wrong with the archive. 

Here is the output when I run tar -tvf to list the files:

<long list of files>
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

It sounds like the archive is corrupt. When I backed it up, I included /etc/ and /home/ on my arch linux, then /media/ubuntu/home/ to get my files from Ubuntu (which are the only ones I really would like to have). The files from Arch can be extracted from the archive, but the ones from Ubuntu would come after the EOF error. Is there some way to extract it and get these files?

---

### Post by mysticrider92 on 2007-12-01
bump... I would really like to solve this.

Could the archive be corrupt with that error message? I have about three copies, so hopefully I can fix at least one...

---

### Post by Cariboo1938 on 2007-12-01
Hi,
same problem here.
Simple Backup Restore does not recognize the backup file in /var/backup.
Is this a general issue in Feisty?
What is to do?:confused:

---

### Post by mysticrider92 on 2007-12-03
Appearantly Sbackup did not actually get the files on my Ubuntu partition like I specified in the configure window. Oh, well, I guess most of the stuff wasn't very importent anyway... I definitely need to pay more attention in the future, but it did not give an error or anything.

---

### Post by eivind on 2008-05-08
I have had similar problems with sbackup, and for now, I have to discourage everyone from using it. The main problem is that it can ruin your backup without giving any notice - see

[https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719](https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719)

and

[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/209314](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/209314)

for more information about problems with sbackup.

---

