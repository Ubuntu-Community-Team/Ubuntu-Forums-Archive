---
title: "firefox links to image files suddenly don't work"
date: 2006-11-18
forum: General Help
---

### Post by kornelix on 2006-11-18
I suspect that the security updates to edgy made available in the last few days have caused a problem in web browsers. Sometimes (not always), web links to image files (.jpg .png) are not displayed, but instead a text window with the URL is displayed. This problem started happening just after I installed the updates, but I cannot be sure if there is a connection.

I tried firefox 2.0, firefox 1.5, and epiphany - all are having this same problem, so it must be in a library module used by all of them. 

Any clues, anyone?

---

### Post by kornelix on 2006-11-18
I think the problem is in libpng12, which was updated in the last few days.

---

### Post by kornelix on 2006-11-20
libpng12 is the problem - verified by replacing following two libraries with earlier versions: /usr/lib/libpng12.so.0.1.2.8 and libpng12.a

Problem was introduced by update to package libpng12-0 on or before 18 Nov. 2006. Forcing the earlier version with synaptic forces deletion of GTK development libraries, and restoring these re-installs the new, defective libpng12-0, so you must bypass synaptic and replace the files directly.

Bug report has been filed with more details: #72411

---

