---
title: "MDADM Question(s) regarding resizing arrays"
date: 2013-01-05
forum: General Help
---

### Post by ltburch2000 on 2013-01-05
I wish to do the following but myresearch has not really lead me to belive if it is possible or not.  I am looking for some conformation that this kind of thing can be done.

1) Establish a 3 disk ext4 raid 5 array with mdadm (this is easy)
2) copy some test files onto the array
3) add a new disk to the array (again easy I think)
4) resize the file system to use the additional disk space from the added disk
5) verify files still OK
6) shrink the file system so one of the drives is no longer needed
7) remove the disk from the array as an active member and add it as a hot spare.

I now want to be back to a normal 3 disk raid array with a hot spare, not a 4 disk array running with a missing disk and a hot spare.

Steps 3 and 7 are the ones that worry me a bit.  Of course all this can be done while the array is not mounted of course, I don't expect any of this to be done online.

Anybody with a little more mdadm experience out there that can clear up is this is feisable?

Ltburch2000

---

### Post by Rsjc741 on 2013-01-05
I'm not really all that familiar with RAID arrays. I have a RAID 0 array for personal use, nor have I used MDADM, but im assuming its a software-based RAID configuration utility.

I do think you can add disks to a RAID 5 array, but as for re-sizing... that might cause an issue.

I would recommend building a RAID 5 array with 4 disks, and keeping all disks online and not mess with partitions.

Or have a 3-disk RAID 5 array online, then keep the 4th disk as a spare in case a disk fails.

The second choice is safer, because RAID 5 only has a 1-disk fault tolerance.

I read that instead of providing degraded speed, MDAM will operate the RAID 5 array as a RAID 1 array.

I'm not an expert though.. so try it out and share it with us. The worse that can happen is a corrupted set of disks.

---

### Post by ltburch2000 on 2013-01-06
Looks possible based on this

[http://webapp5.rrz.uni-hamburg.de/SuSe-Dokumentation/manual/sles-manuals_en/manual/raidresize.html](http://webapp5.rrz.uni-hamburg.de/SuSe-Dokumentation/manual/sles-manuals_en/manual/raidresize.html)

---

