---
title: "Stat Command - Output showing different timezone for modify date"
date: 2018-09-16
forum: General Help
---

### Post by Alan5127 on 2018-09-16
Hi All,

I have a system running Ubuntu 16.04 LTS where I get an output from the 'stat' command showing one timezone for the modify date, and another for the change and access dates:

```
$ stat Dir_Alan/
  File: 'Dir_Alan/'
  Size: 0             Blocks: 0          IO Block: 4096   directory
Device: 821h/2081d    Inode: 131         Links: 1
Access: (0777/drwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2018-09-15 15:05:28.035436700 +1200
Modify: 2018-01-01 01:00:00.000000000 +1300
Change: 2018-09-15 15:05:23.350780500 +1200
 Birth: -


```

I have tried setting the 'modify' date to be 1 Jan 2018 to see if that fixed it, but it still shows as timezone +1300, whereas the access and change timezones are +1200.

I figured it might be something about the drive (this was first noticed on an external USB drive), but some other directories (including in my home directory that is on the internal HDD) exhibit the same thing.

On the other hand, if I run 'stat' against the root folder, I don't see the issue.  For example, from /:

```
$ stat bin
  File: 'bin'
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d    Inode: 786435      Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2018-09-14 00:29:07.512776225 +1200
Modify: 2018-07-31 18:47:25.669009044 +1200
Change: 2018-07-31 18:47:25.669009044 +1200
 Birth: -

```


It doesn't *appear* to be causing any issues, but it seems odd, so I am wondering what could be causing it?


Thanks,

Alan.

---

### Post by The Cog on 2018-09-16
Daylight savings time, at a guess.
All the timestamps you posted except "Modify: 2018-01-01 01:00:00.000000000 +1300" happened during the summer.

---

