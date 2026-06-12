---
title: "Samba only works after explicitly restart the service"
date: 2006-11-10
forum: General Help
---

### Post by vairoj on 2006-11-10
I setup Samba file server on Ubuntu Server 6.06 using Domain security. The problem is that after restart the server, trying to browse to its share directory from other Windows client popup the following error message:

\\Arctic is not accessible.

There are currently no logon servers available to service the logon request.

However, if I explicitly restart Samba daemon using:
/etc/init.d/samba restart

The problem will just go away.

Does anyone what is the cause of this problem?

---

### Post by temcat on 2006-11-10
This problem is not new, and AFAIK there is stil no solution for it. Very annoying. That was one of the reasons I gave up on running Windows in VMware.

---

### Post by vairoj on 2006-11-13
That's awful. If this is a known issue without any solution, I wonder how does all Linux boxes running Samba workaround the issue?

---

### Post by temcat on 2006-11-13
> **vairoj said:**
> That's awful. If this is a known issue without any solution, I wonder how does all Linux boxes running Samba workaround the issue?

Well, I suppose that this issue with Samba is specific to Ubuntu, not Linux/Samba in general.

---

