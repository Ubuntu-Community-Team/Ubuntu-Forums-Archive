---
title: "Specify a network drive as a target in Duplicity"
date: 2016-06-22
forum: General Help
---

### Post by lile001 on 2016-06-22
I would like to use Duplicity to backup to a drive on a windows share.  

I have tried to do this backup using Deja Dup, however it fails.  Although Deja Dup claims it has completed a backup yesterday, there are no files in the specified backup location.  Deja Dup has no more information, being a brain-dead-simple gui, so if something goes wrong one is left scratching their head. 

I'd like to tell Duplicity directly to do the backup, but I don't know how to specify the backup location.  


The location I'd like to back up to is a 1 TB drive on a windows computer accessible through Samba:

smb://192.168.0.7/f/[some folder]/[some other folder]

In Nautilus it appears this location is mounted, although I do not see it listed in /media 

Using this smb: format as a target URL directly in Duplicity results in an error "Scheme not supported in URL"  

How do I specify this as a backup target URL?

---

