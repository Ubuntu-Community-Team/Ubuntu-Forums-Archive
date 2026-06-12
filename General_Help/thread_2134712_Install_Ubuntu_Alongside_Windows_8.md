---
title: "Install Ubuntu Alongside Windows 8"
date: 2013-04-11
forum: General Help
---

### Post by Cypher32 on 2013-04-11
When I try to go to UEFI mode it says no boot options any idea?

---

### Post by oldfred on 2013-04-12
Moved to your own thread. Other thread was resolved. Did you review those instructions.

We need more info on what system. If an Ultrabook you have Intel SRT which uses RAID, or may have other issues.

Post this from terminal in live installer terminal.
       sudo parted /dev/sda unit s print
If you have more than one drive this also:

 sudo parted /dev/sdb unit s print

---

