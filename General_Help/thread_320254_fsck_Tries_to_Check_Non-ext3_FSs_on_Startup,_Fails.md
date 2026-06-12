---
title: "fsck Tries to Check Non-ext3 FSs on Startup, Fails"
date: 2006-12-17
forum: General Help
---

### Post by nrwilk on 2006-12-17
During the automated check that occurs every few startups, my machine seems to now be checking my non-ext3 partitions.  Two are ntfs, one is "vfat."  I added "noauto" to the mount option of each of these partitions in fstab, but this has not helped.  Obviously, the partitions fail the check, and throw the entire startup process off.

Can anyone suggest a way to exclude these partitions from fsck checks?

Thank you :) 

nrwilk

---

### Post by taurus on 2006-12-17
The last two numbers for vfat & ntfs entries need to be "0  0" and nothing else...  Look in /etc/fstab to make sure that's what they are.

---

### Post by nrwilk on 2007-01-03
Upon checking those columns, I found that they did have the incorrect values.  I changed them as you suggested, and that has cleared up the problem.

Unfortunately, it has made me aware of another, related problem.  Because this new problem does not fit under the title of the thread, I'll begin a new thread with an appropriate title.

Thank you! :) 

nrwilk

---

