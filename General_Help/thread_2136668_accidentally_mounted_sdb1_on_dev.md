---
title: "accidentally mounted sdb1 on /dev"
date: 2013-04-18
forum: General Help
---

### Post by AmbiguousOutlier on 2013-04-18
I messed up I just assumed it would mount as /dev/sdb or something, I changed fstab and did mount -a! I can't do anything now. Any commands that require root, error, so I can't open fstab back up to change it.

---

### Post by cortman on 2013-04-18
Ouch.
Someone more knowledgeable than me may suggest something to fix it, but I would just boot from a live CD, copy your data off the computer HDD onto an external HDD, and reinstall.

---

### Post by Cheesemill on 2013-04-18
If you boot from a Live CD you can edit the fstab file of your broken system back to what it was before you changed it.

---

