---
title: "Compile a list of double backed up files/directories"
date: 2019-11-10
forum: General Help
---

### Post by thunderbirdje on 2019-11-10
Hi everyone,

Over the years (30+) I have made backups on external hard drives, thumb drives and in older days CD-ROMs.

Most files should be backed up on my central NAS by now. I would like to check if that is the case or not in a quite automatic way.

I sadly have the habit to move files to a different directory or sometimes rename them. Which makes it hard to run “just a comparison by file/directory name”.

I am looking for a tool able to compile a list of identical files telling which files are double (copy) and which ones are not (needs to be copied)? 

The aim is to clean out all the external drives. And eventually backup op the NAS to external drives or cloud services.

Thanks a lot for any advice!

---

### Post by TheFu on 2019-11-10
Sounds like a mess.
1 copy isn't a backup.
For each file, which storage location is the "storage of record?"  That is what you should backup.  If there is only 2 copies, it isn't a backup in my mind.  
* Original, production copy.
* Versioned, backup on local storage (rdiff-backup to get versioned data and permissions)
* Versioned, backup on off-site storage (rsync from the local backup)
Any offsite backups must be encrypted. Never trust the encryption layer provided by the backup vendor. Always do it yourself with LUKS or gpg or openssl.

To clean up the production source copies, use a file deduplication tool like **fdupes**.  There are about 10 of these tools.  I wrote one a few years ago in perl after seeing a question on /.  Mine is a hack and just makes a list of duplicate files after running a few different types of comparisons to ensure they really are duplicates regardless of the filename.  Turned out that list still creates a huge hassle to cleanup, at least for me.
The manpage for fdupes:
```
NAME
       fdupes - finds duplicate files in a given set of directories

SYNOPSIS
       fdupes [ options ] DIRECTORY ...

DESCRIPTION
       Searches  the  given path for duplicate files. Such files are found by
       comparing file sizes and MD5 signatures, followed  by  a  byte-by-byte
       comparison.

```
Having a list of 2,000 files with duplicates should be expected.

---

### Post by HermanAB on 2019-11-10
There are several programs with a 'duplicates' function of sorts: rsync, fdupes, fslint, hardlink...

When all else fails, run 'find' with 'sort' and redirect the output to a text file.

---

### Post by SeijiSensei on 2019-11-10
diff works for binaries as well as text files. With the -q option it reports only files that differ.

---

