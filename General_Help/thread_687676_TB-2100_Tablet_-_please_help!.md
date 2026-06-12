---
title: "TB-2100 Tablet - please help!?"
date: 2008-02-04
forum: General Help
---

### Post by viciouslime on 2008-02-04
There only seems to be one post on the forums that references this tablet and it says that it works. But when I plug mine in, it does nothing. Anyone got any ideas?

---

### Post by pointone on 2008-02-04
Try editing /etc/X11/xorg.conf and uncommenting the tablet-related lines. You could also try automatically reconfiguring X by running dpkg-reconfigure xserver-xorg.

---

