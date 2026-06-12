---
title: "Removing unused modules"
date: 2005-09-04
forum: General Help
---

### Post by AndreAPL on 2005-09-04
hi there. i want to remove unused modules from my kernel. can i simply erase them from /lib/modules/kernelx ?
thanks

---

### Post by dabear on 2005-09-04
Hi, please read this post: [http://ubuntuforums.org/announcement.php?f=58](http://ubuntuforums.org/announcement.php?f=58)

---

### Post by az on 2005-09-04
I moved the thread.


There probably would be better ways to free up some disk space.  And make sure you do not erase any modules that you would need in the future if you ever add some hadware to your system.

You would also have to hold the package version so that you do not update your kernel the next time there is a bug fix or security fix.  In that case, the package would get reinstalled and all the modules you deleted would be back.  As it is, that would happen the next time you update and the kernel package has been updated.


Now, do you really want to prevent yourself from getting bug and security fixes?

---

