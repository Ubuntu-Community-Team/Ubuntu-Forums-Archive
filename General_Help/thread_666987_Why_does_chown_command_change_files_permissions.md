---
title: "Why does chown command change files permissions?"
date: 2008-01-13
forum: General Help
---

### Post by dearvoid on 2008-01-13
I have an executable file with set-user-id bit set. After I chown'ed the file, the set-user-id bit was removed! Why?

# ls -l doit
-rwsr-sr-x 1 root root 23 2007-08-16 14:30 doit
# chown root:root doit
# ls -l doit
-rwxr-xr-x 1 root root 23 2007-08-16 14:30 doit
#

Note that my system is Ubuntu 6.06 (i686).

---

### Post by jflowers on 2008-01-14
Although I am not an expert, it is probably that the the default permissions are (rwx) and by changing the owners of the file, it is up to the new owner to create the specific set-user-id.  I would guess that you could modify this by just doing chmod (u or o) + s.   I hope this helps.

---

### Post by dearvoid on 2008-01-14
> **jflowers said:**
> Although I am not an expert, it is probably that the the default permissions are (rwx) and by changing the owners of the file, it is up to the new owner to create the specific set-user-id.  I would guess that you could modify this by just doing chmod (u or o) + s.   I hope this helps.

Thanks. Another chmod will fix this problem. I just don't know why chown will do the chmod thing. Other systems like FC3 don't have this issue. It cause one of my script not to work fine. I spent quite a while to find it out. And I strace'd the chown command and found no chmod() invocation.

---

