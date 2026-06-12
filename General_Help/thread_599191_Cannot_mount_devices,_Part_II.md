---
title: "Cannot mount devices, Part II"
date: 2007-11-01
forum: General Help
---

### Post by fdv1 on 2007-11-01
[This is the workaround for the infamous hal-storage-removable-mount-all-options refused uid 1000 error.]("http://ubuntuforums.org/showthread.php?t=598785")

The non-solutions are detailed in it. 

I have used workaround #1, but am still having two problems.

Problem #1. [Options on three drives are greyed out, and on one, a permissions tab is missing altogether!!?! This is an animated GIF to illustrate the problem.]("http://vorck.com/images/mountproblem2.gif")

Problem #2. This kludge of assigning devices that should be recognized as valid media to directories in mnt, and then chmoding and editing fstab... doesn't this embarass anyone else trying to "sell" Linux? **Come ON**, even Windows gives fewer problems recognizing devices! I'd like to be able to see media devices as media devices... not assign them to directories. **Am I really all alone on this one?** Everyone really is content to have to take 20 minutes to create a kludge that only half-works, and recognizes some, but not all, drives?

Thoughts on #'s 1 and 2?

---

### Post by fdv1 on 2007-11-01
Ok...

Then what about commenting the code out,

Workaround #2
REMOVE this:
+ if (!invoked_by_uid || strcmp(invoked_by_uid, "0"))
+ if (!privilege || strcmp (privilege, "hal-storage-removable-mount"))
+ permission_denied_privilege (privilege, invoked_by_uid);

What file do I remove from??

Any help appreciated...

---

### Post by fdv1 on 2007-11-01
Where is the most appropriate subforum to post this kind of question?

---

