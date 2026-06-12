---
title: "Version Check"
date: 2008-05-13
forum: General Help
---

### Post by bpinterconnect on 2008-05-13
We are attempting to determine if our system machine is running Ubuntu server or desktop.  Is there an easy way to determine what version of software you're running?
Help Please......

---

### Post by BlueSkyNIS on 2008-05-13
Is looking at "System -> About Ubuntu" of any help?

---

### Post by lswest on 2008-05-13
well, a few ideas (i can't check if they say if it's desktop or not) but ```
lsb_release -a
uname -a
``` may tell you, and the easiest check is...when you installed Ubuntu did you install it from a fully-functional desktop environment off the CD and did it install a GUI?  If so, it's the Desktop version.  Ultimately the Server and the Desktop systems are the same setup, with a few changes (such as the server can install apache and such from the initial setup, and has no GUI, whereas the Desktop has no apache but a GUI).

---

