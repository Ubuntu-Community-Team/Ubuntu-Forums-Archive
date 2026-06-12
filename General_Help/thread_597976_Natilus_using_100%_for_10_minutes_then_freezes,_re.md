---
title: "Natilus using 100% for 10 minutes then freezes, resulting me in restarting X."
date: 2007-10-30
forum: General Help
---

### Post by blithen on 2007-10-30
A common problem? How do I stop it from happening? I was doing nothing but organizing files into certain folders and such when this happened...

---

### Post by Can+~ on 2007-10-30
I usually suspect from tracker, try disabling indexing services, since those are the most resource-eating processes. (System > Preferences > Indexing)

If that does not work, look for any log in the var/log folder (ls -R /var/log | grep nautilus).

---

### Post by blithen on 2007-10-30
w00t thanks man!

---

