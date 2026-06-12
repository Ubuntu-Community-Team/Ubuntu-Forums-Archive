---
title: "2 drives - one mount point?"
date: 2007-02-14
forum: General Help
---

### Post by vampiric_blade on 2007-02-14
Hi,

I am running a mythtv box with my pvr150 and want to add a 2 more hdds to store my shows and movies.   Is it possible to mount both new drives under one mount point?  Would I just be able to "mount /dev/xxx /media/videos" for both drives?

Thanks.

---

### Post by lamego on 2007-02-14
You will need to use LVM to be able to aggregate multiple disks on a single mount point.
I don't know any good LVM tutorial to recommend...

---

### Post by vampiric_blade on 2007-02-14
It seems like the alternate 6.10 install cd lets you set up lvm when installing.  I'll reinstall as I am not too far into it anyway.  

Thanks for the help!

---

