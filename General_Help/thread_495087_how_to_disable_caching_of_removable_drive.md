---
title: "how to disable caching of removable drive?"
date: 2007-07-07
forum: General Help
---

### Post by myoclonic on 2007-07-07
Can someone tell me how I can make it so that when I perform file operations on a USB flash drive, the changes are "committed" right away?  A few times when I've renamed a file on a flash drive and then pulled out the drive without properly unmounting it, I found that the file didn't actually get renamed.  Basically, I often forget to unmount properly and I'd to avoid these errors.  Thanks!

---

### Post by geraldm on 2007-07-07
Executing the umount command gets the job done.
If you do not change your habits, then use a script to:
1) rename the file
2) umount
3) (mount ..)
.. for each file renaming.  Easier to change the habit though.

Gerald

---

