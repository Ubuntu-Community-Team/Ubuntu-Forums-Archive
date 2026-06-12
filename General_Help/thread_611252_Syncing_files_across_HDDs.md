---
title: "Syncing files across HDDs?"
date: 2007-11-12
forum: General Help
---

### Post by velozoom on 2007-11-12
Wondering if this is possible....

I was told when I bought my HP laptop that it supported hardware RAID.  They lied, of course, or the salesman had no clue about what I was talking about but I digress....I don't want to set up software-based mirroring, but I would like to set up some sort of automatic synchronization of specific files/directories (mostly my /home/[username] directory where all my really important files are) across the two HDDs in my laptop.  

Is there a way to set up this sort of file synchronization in Gutsy?  Thanks in advance......

p.s.- if there is a reason to consider software RAID in linux I will, but in my job as a windows network admin i've learned the hard way that software RAID is bad juju.....

---

### Post by volksman on 2007-11-12
Software RAID does rarely work.  I, like you however, feel it is mostly a waste of time.

Your two best options for synchronization are rsync or flyback.

Flyback uses rsync to take "snapshots" of your system.  Very similar to shadow copies in windows combined with system restore points.  However there is little overhead and all you need is a drive to store your snapshots on.

rsync is a very robust copy/sync mechanism that will only transfer "differences" between two file systems.

Depending on what you want either of those will likely do the trick.

[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)  <-  Flyback site

rsync is available with apt:

sudo apt-get install rsync

---

### Post by velozoom on 2007-11-12
grazie!  I'll look into those immediately.

---

