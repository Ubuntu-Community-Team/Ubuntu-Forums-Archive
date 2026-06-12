---
title: "a little install problem"
date: 2008-01-25
forum: General Help
---

### Post by whi on 2008-01-25
When I try to install, I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do I need to do for fiks this problem...

---

### Post by ugm6hr on 2008-01-25
> **whi said:**
> When I try to install, I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do I need to do for fiks this problem...

Have you tried doing what is suggested?

```
sudo dpkg --configure -a
```

This problem normally results from a partial installation of updates / new software.

---

### Post by whi on 2008-01-25
trying that now... that did not work last time i tried

---

### Post by whi on 2008-01-25
it works now... thank you

---

### Post by ugm6hr on 2008-01-25
> **whi said:**
> it works now... thank you

Glad it works...

Perhaps you could mark this thread as solved (see the link near the top labelled Thread Tools),  This is good for the future users who stumble across the same problem, so it is worthwhile you knowing how to do this yourself.

---

