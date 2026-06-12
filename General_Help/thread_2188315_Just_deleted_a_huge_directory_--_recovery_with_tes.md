---
title: "Just deleted a huge directory -- recovery with testdisk"
date: 2013-11-16
forum: General Help
---

### Post by theKuch on 2013-11-16
Hi.

I just deleted a very large directory with many sub-directories under it, each with lots of files.

I ran testdisk and was able to find the directory marked in red.

I used 'C' to copy the deleted directory into another partition. It copied, but the directory was blank.

When I tried to have a look at what was in the original deleted directory, it is blank.

I haven't done anything on this disc since I deleted it.

-------------------------------------------------
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
 1 P Linux                    0  32 33 243153  30 13 3906252800 [5DIII]
Directory /

>drwxrwxrwx     0     0      4096 16-Nov-2013 17:51 .
 drwxrwxrwx     0     0      4096 16-Nov-2013 17:51 ..
 drwxr-xr-x  1000  1000     12288 21-May-2010 14:01 AvielBarmi
 drwx------  1000  1000      4096  1-Aug-2013 19:01 .Trash-1000
 drwxrwxr-x  1000  1000      4096  5-Nov-2013 14:42 Freddy
 drwxr-xr-x  1000  1000      4096  5-May-2013 22:06 KuchCo
 drwxr-xr-x  1000  1000      4096  5-May-2013 14:22 MenachemCo
 drwxr-xr-x  1000  1000      4096  3-May-2011 16:15 MichalDovWedding
 **drwx------  1000  1000         0 16-Nov-2013 17:53 Photography**
 drwxrwxr-x  1000  1000      4096  3-Jun-2013 14:20 TalHoniWedding
 drwxr-xr-x  1000  1000      4096  9-Jun-2011 18:41 xBlogs
 drwx------  1000  1000      4096 26-Sep-2013 20:25 Trip
-------------------------------------------------

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
 1 P Linux                    0  32 33 243153  30 13 3906252800 [5DIII]
Directory /Photography

No file found, filesystem may be damaged.
-------------------------------------------------

Any help would be greatly appreciated.

Thanks.

Menachem

---

### Post by tgalati4 on 2013-11-16
```
man photorec
```

It's possible that the file system did some housecleaning, even though you did not use the disk after the delete.  Run *photorec* and see how many files it can recover.

Testdisk is telling you that the disk is damaged.  Why did you delete the files in the first place?

---

### Post by theKuch on 2013-11-17
Thanks. I deleted the directories because I'm stupid is the short answer. Unfortunately there are a few thousand files here, both RAW and JPG. I have all of these backed up. I need the TIF files I created in the last few days. I think it will take me longer to work through the files without names from a carver than to recreate them. So I guess I'll reconstruct from backup and rework what I already did. You never know -- I may end up with something better.

Thanks again.

Menachem

---

