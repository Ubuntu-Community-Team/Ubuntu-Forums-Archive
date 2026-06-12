---
title: "Hellanzb rar/unrar issues"
date: 2007-10-13
forum: General Help
---

### Post by rosarch on 2007-10-13
Hi, I am currently having issues with rar/unrar in hellanzb

When I download one small file using hellaworld or zussaweb it downs and unrars without an issue.

If I down a large file or multiple files then unrar/rar seems to hang and nothing gets unrarred, I can see it in ps aux but it doesn't seem to be doing anything and just sits there, in the end I have to unrar it myself

Has anyone else come across this?

Cheers
Rosarch

---

### Post by kditty on 2007-10-14
im having a weird problem with hellanzb myself. this is what happens:

hellanzb v0.13 (config = /etc/hellanzb.conf)
(uns) Opening 8 connections...
hellanzb - Now monitoring queue...
Resuming: deletedforprivacy
Parsing: deletedforprivacy.nzb...
Parsed: 116 files (2445 posts), 1499.6MB
Skipped (on disk): 115 files and 23 segments, 1499.0MB
Queued: 645KB
[1] deletedforprivacy.r08 - 99% @ 0.0KB/s
[2]
[3]
[4]
[5]
[6]
[7]
[8]
[Total] 0.0KB/s, 0 MB queued, ETA: 00:00:00

seems like a lot of the downloads just hang, its also not unraring everything. it started when i accidentaly upgraded to v0.13 because v 0.09 never gave me a single problem ive used that for over a year and a half

---

### Post by kditty on 2007-10-14
try this out, seems to have worked for me. also read on in that thread for a few specifics on what you need to change in config file to use unrar.

reinstall:
[http://ubuntuforums.org/showpost.php?p=2510539&postcount=152](http://ubuntuforums.org/showpost.php?p=2510539&postcount=152)

then continue reading thread for other issues:
[http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb&page=16](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb&page=16)

---

### Post by rosarch on 2007-10-17
Thanks Kditty :-)

---

