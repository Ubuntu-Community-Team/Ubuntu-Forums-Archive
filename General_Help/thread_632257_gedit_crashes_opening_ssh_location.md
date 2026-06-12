---
title: "gedit crashes opening ssh location"
date: 2007-12-05
forum: General Help
---

### Post by alfanerd on 2007-12-05
Hi,

After yesterday's upgrades (libcairo, network-manager,firefox, etc), gedit can no longer open documents in ssh locations. e.g.:

me@my-desktop$ gedit ssh://me@host/path_to_file/README.txt
Floating point exception (core dumped)

Any ideas?

---

### Post by alfanerd on 2007-12-05
Problem solved.
Looking at this thread [http://ubuntuforums.org/showthread.php?t=630859&highlight=gedit](http://ubuntuforums.org/showthread.php?t=630859&highlight=gedit) made me suspect my .fonts directory. I removed it and now gedit works again.

---

