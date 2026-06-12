---
title: "How do you restore just one particular file using sbackup restore?"
date: 2008-05-29
forum: General Help
---

### Post by ubnewbie2 on 2008-05-29
I have been running sbackup regularly, and it has worked well.  All my backups are on a data drive, which was a good choice because my main boot drive has died.  I have rebuilt my system, and installed Hardy again, and now I want to restore, just certain of the files from my backups.

For example, I want the latest version of a file called hints.txt, which was in my home directory, and I used to add to it from time to time, usually a few times a month.

So, I installed sbackup again, and ran the restore app.  I select 'Use custom' and point it to my backup directory.  Now I have to select the backup set, but I don't know which one has the latest version of this file.  The latest full backup has one version, but there are quite a few incrementals since then.  Do I have to open each incremental backup, one by one, looking to see if a later copy exists?  

Does the program have any way to specify a file name, and let it find all the versions it has in the backups directory, then let me select which version (by date) to restore? Failing that, is there any other addon or utility for sbackup that will help?

Another small problem is that the list of files it offers when I select the latest full backup and open up my home directory, is NOT sorted  so it's damn hard to find the file I want in the long list.

So, if the answer to my questions is  no, the program is not capable of doing what I want  can anyone suggest a better alternative to Simple Backup (sbackup)

---

### Post by vagueblur on 2008-05-31
As far as I can see, you have to do it all manually. :-(

I'm really disappointed with sbackup, I'm in the same situation as you - I was using sbackup and then lost a lot of files. Now I'm trying to restore and it looks like it won't automatically restore the incremental backups. I think you have to go through and restore each one separately.

The size of my full backup is 24GB and the restore program can't handle it... it restores some files and leave a temp directory with some more files in it.

I tried unzipping manually but then when you unzip the incrementals it doesn't handle the deleted/moved files.

I'm thinking about a really simple rsync script once I get this mess sorted out.

---

### Post by ubnewbie2 on 2008-05-31
Yes, a simple script will achieve a backup of sorts, but sbackup seemed to have so much promise.  When I saw the logarithmic purging of old backups, I never imagined it would be so limited on the restore side.

My main hope now is that someone has written a much smarter restore utility for it.

---

