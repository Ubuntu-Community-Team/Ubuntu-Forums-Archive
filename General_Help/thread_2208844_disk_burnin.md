---
title: "disk burnin"
date: 2014-03-02
forum: General Help
---

### Post by Wray on 2014-03-02
I have a disk that was running Win 7 that crashed.  Smart data reports 11 bad sectors.

Bottom line, i don't trust the disk
Back in the day about a million yrs ago we had programs (propiatary, of course) that would Burn in the disks by running  a suite of read, write, seeks, etc, continuously for long periods of time, selected by the user.
At the end of the testing, read,write,seek errors were reported.

Does anybody know of anything remotely similar in Linux.

---

### Post by linuxonbute on 2014-03-02
You could use badblocks.

```

badblocks   -p 10 /dev/hda 

```
which would scan the disc 10 times in read only mode.
You can only use it on discs which are not mounted so
probably booting from a live disc would be the way to go.

Look at man badblocks  as it gives you all the possible options 
but note that you must not use the -w option on a disc you have any information on you want to keep.
For that you could use the -n option which is slow but does a non destructive read/write test

---

