---
title: "Error when updating"
date: 2008-01-22
forum: General Help
---

### Post by Jeffrey.Lee.Li on 2008-01-22
When I update, I got the following error hints.
----------------------------------------------------------------------------------------------------------
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) gutsy-proposed/main Packages                  
  Sub-process bzip2 returned an error code (2)
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) gutsy-proposed/universe Packages              
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) gutsy-proposed/multiverse Packages            
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) gutsy-proposed/main Sources                   
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) gutsy-proposed/restricted Sources             
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) gutsy-proposed/universe Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) gutsy-proposed/multiverse Sources
Fetched 94.2kB in 1m50s (856B/s)
Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
----------------------------------------------------------------------------------------------------------

What's wrong with ubuntu server or my own machine?

Any contribution is welcome~~~:)

---

### Post by notepad on 2008-01-22
ouch! can i suggest you try using the main repository instead of the local one?
i notice you are using cn.archive.ubuntu.com
i had some problems with trying to install a particular package when i was trying to use the australian source instead of the main source.
change it in system > administration > software sources
download from ... main server

---

### Post by Jeffrey.Lee.Li on 2008-01-22
> **notepad said:**
> ouch! can i suggest you try using the main repository instead of the local one?
i notice you are using cn.archive.ubuntu.com
i had some problems with trying to install a particular package when i was trying to use the australian source instead of the main source.
change it in system > administration > software sources
download from ... main server

Thanks~~~

So you're saying that the problem is not with apps in my own os?

Well, that's good. I'll change my sources.list to solve it~~~:)

---

