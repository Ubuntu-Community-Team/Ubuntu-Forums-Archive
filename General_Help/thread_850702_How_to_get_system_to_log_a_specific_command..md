---
title: "How to get system to log a specific command."
date: 2008-07-05
forum: General Help
---

### Post by mempman on 2008-07-05
Is it possible to have syslog monitor access to a specific file, or will i have to resort to some 3rd party software because what I am trying to monitor is independent of system-internal related stuff?

---

### Post by ghostdog74 on 2008-07-05
what or what command are you trying to monitor?

---

### Post by mempman on 2008-07-05
> **ghostdog74 said:**
> what or what command are you trying to monitor?


I am trying to monitor read access on a specific file, that can be read by anyone.

---

### Post by ghostdog74 on 2008-07-05
it can be done using auditd. See [here](http://librenix.com/?inode=10248)for more

---

