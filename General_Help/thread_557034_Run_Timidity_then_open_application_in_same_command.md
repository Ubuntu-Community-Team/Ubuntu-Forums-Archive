---
title: "Run Timidity then open application in same command"
date: 2007-09-22
forum: General Help
---

### Post by acl123 on 2007-09-22
Hi, a few of my applications, eg. Guitar Pro, require timidity to be run before the application will have sound. I need to execute "timidity -iA -B2,8 -Os &" in a terminal, then leave that terminal open while I use Guitar Pro.

How can I setup my Guitar Pro shortcut in Gnome's Application menu so that it runs timidity as well?

I have tried editing the shortcut's properties to include both commands separated with a semicolon, but this doesn't work. Guitar Pro still opens, but the sound doesn't work.

---

### Post by MJN on 2007-09-22
Try **&&** instead of the semi-colon - this basically means 'execute the first command, and if it succeeds execute the second' (conversely, **||** is the opposite i.e. execute the second if the first fails).

Mathew

---

### Post by acl123 on 2007-09-24
Cool that works better

---

