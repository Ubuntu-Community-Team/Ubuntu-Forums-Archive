---
title: "ulimit"
date: 2007-12-17
forum: General Help
---

### Post by selwyn on 2007-12-17
Hi,

I am having trouble increasing the number simultaneous file processes via ulimit (e.g. ulimit -n 2000) for a regular user, triggering the following error: 
-bash: ulimit: open files: cannot modify limit: Operation not permitted

I can however increase this to 20000 for a root shell, but I dont want to run production code as a root user...

I have changed /etc/security/limits.conf to the settings below, but it still wont take effect even after rebooting:

selwyn           hard    nofiles         20000

Any help warmly received.

Thanks,
Selwyn

--
System: Dapper AMD64
--

---

