---
title: "source /etc/profile don't work"
date: 2013-02-26
forum: General Help
---

### Post by crossbower on 2013-02-26
Hello,
I  changed umask value 
**$ umask 0044**

I'm trying to reload the umask value configuration (0022) without exit of  shell session:
**$ source /etc/profile  **

but don't work.
How can I do?

Thanks in advanced

---

### Post by rnerwein on 2013-02-26
> **crossbower said:**
> Hello,
I  changed umask value 
**$ umask 0044**

I'm trying to reload the umask value configuration (0022) without exit of  shell session:
**$ source /etc/profile  **

but don't work.
How can I do?

Thanks in advanced
hi
load the /etc/profile into an editor and have a look at those sentences:

# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.

ciao

---

