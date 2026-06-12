---
title: "how to not automount partition"
date: 2008-01-27
forum: General Help
---

### Post by Raccoon1400 on 2008-01-27
My computer has a dell utility partition, which ubuntu automatically mounts. This is not required. How to i tell the computer not to mount this partition on boot? filesystem is fat.

---

### Post by bodhi.zazen on 2008-01-27
edit /etc/fstab and place noauto in the options field

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

