---
title: "Bypass ifstate"
date: 2006-09-18
forum: General Help
---

### Post by prabesh on 2006-09-18
Hello. When my computer undergoes a hard reboot, the ifstate file never gets cleared. Therefore, my interfaces are not automatically configured (as ifup thinks they are up). Is there any way to bypass this?

Prabesh

---

### Post by yopnono on 2006-09-19
well you can always use ```
ifup -a --force
``` to force the network interfaces to get configured.

And if you like, put it in the ```
/etc/rc.local
``` script file to run it at boot.

---

