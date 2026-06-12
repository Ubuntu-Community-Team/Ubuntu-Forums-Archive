---
title: "zfs from freebsd 11.2"
date: 2018-09-07
forum: General Help
---

### Post by makke on 2018-09-07
Hi, I'm thinking of migrating from Freebsd 11.2 to Ubuntu and have the following question:

Has anyone imported an zfs pool created on Freebsd 11.2 with success, or would it be recommended to recreate the pool?

When searching for it, I only find old posts.

Regards,
Makke

---

### Post by TheFu on 2018-09-07
IDK.

Anything you can't afford to loose, you should have a 100% know-you-can-restore backup. Using ZFS doesn't negate that. Using RAID doesn't negate that.

---

### Post by makke on 2018-09-08
Sure, but the question is if I should assume that I will have to import all data once again, it takes alot of time, or if it would be possible to import the pool and just keep running, then I could do the switch from FreeBSD to Ubuntu over an evening, if I need to move all data it would take about a week, guess I just have to try the LiveCD and see how it goes.

BR,
Makke.

---

### Post by TheFu on 2018-09-08
I would never **assume** anything.  Then I'd be pleasantly surprised if it all "just works".
[https://unix.stackexchange.com/questions/102361/is-a-zfs-storage-array-portable-across-operating-systems-cpu-architectures](https://unix.stackexchange.com/questions/102361/is-a-zfs-storage-array-portable-across-operating-systems-cpu-architectures) suggests "fingers crossed" but guarantees don't exist.  The responses all used ZFS-FUSE, which would be slow for long-term needs, but if the goal was to get some data, quickly, then it probably isn't THAT terrible.  FUSE can be slow, like 50% slower than kernel mounts.

You've probably already seen that link. Sorry I can't reassure.

---

### Post by makke on 2018-09-11
Thanks! I had not found that link.

I understand that you can't reassure, but I will try to split the mirrors, and then create a new pool under Linux, then mount the old along side that, and move all the data.
No worries if it all goes south, I do have backups elsewhere, just neat if I could do with internal copy due to speed.

Thanks again, never thought of the search term "portable", which makes sense now.

/Makke

---

