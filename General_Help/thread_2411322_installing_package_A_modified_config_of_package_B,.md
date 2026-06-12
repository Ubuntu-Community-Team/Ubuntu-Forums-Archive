---
title: "installing package A modified config of package B, purging A left B broken"
date: 2019-01-28
forum: General Help
---

### Post by LazyBoy on 2019-01-28
So I tried freeipa recently and after I purged it, ssh didn't work anymore.  /etc/ssh/ssh_config had been modified to reference an executable that wasn't on the machine.  (I don't really know if it worked *while* freeipa was installed.  I don't usually ssh *out* of this machine.)

Anyway, thanks to etckeeper, it was easy to fix.  But it made me wonder if there was a general policy.  Should pkg A modify configs for pkg B?  Should pkg A repair those configs when it's removed or purged?

---

### Post by TheFu on 2019-01-28
Was this the client or the server?

You should report the issue to the freeIPA team, especially if you can reproduce the issue and show exactly what has changed.  FreeIPA is a ported package from the RPM world and it was a non-trivial port.  The client has been around much longer.  

Proper system, versioned, backups would have allowed recovery too.  With etckeeper, can't you see what changed over time?

---

