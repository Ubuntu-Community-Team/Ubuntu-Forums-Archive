---
title: "Managing updates from the command line"
date: 2008-06-24
forum: General Help
---

### Post by yang on 2008-06-24
Is aptitude update; aptitude safe-upgrade (or full-upgrade?) actually equivalent to using update-manager?  If so, how do I tell whether a restart was required afterward (as seems to frequently be the case with updates applied via update-manager)?  Thanks in advance!

---

### Post by avtolle on 2008-06-24
Using aptitude, it will tell you that a restart is required in the console window. Generally, a restart is required when the kernel is updated; there are a few other specific circumstances (almost always affecting the kernel), FYI.

---

### Post by yang on 2008-06-24
Thanks.  And the command to use is safe-upgrade, yes?

---

