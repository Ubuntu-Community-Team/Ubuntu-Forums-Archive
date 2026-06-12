---
title: "Need Assistance with a startup command"
date: 2007-12-26
forum: General Help
---

### Post by nixxofugi on 2007-12-26
Hello, I am attempting to add the following to the startup scripts that are run when booting the computer.

sudo hdparm -B 255 /dev/hda

does anyone have any idea where I could insert this line to have it run when booting, possibly even before a user logs in...

Greatly Appreciated...

Rob

---

### Post by dagnabit dang doohickey on 2007-12-26
/etc/hdparm.conf

Check out the man page if needed: man hdparm.conf

---

