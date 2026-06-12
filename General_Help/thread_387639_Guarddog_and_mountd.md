---
title: "Guarddog and mountd"
date: 2007-03-18
forum: General Help
---

### Post by manoj_paul_joseph on 2007-03-18
Hi,

I am trying to configure iptables using guarddog. I need to permit access to mountd.

Mountd binds to a different port on every boot. I do not want to permit access to a range of ports. Is there any way I can tell guarddog (or iptables) to permit access to the port that mountd (and nlockmgr) binds to?

Thanks in advance.

-Manoj

---

### Post by r4ik on 2007-03-18
Perhaps this helps ?

[http://www.simonzone.com/software/guarddog/manual2/index.html](http://www.simonzone.com/software/guarddog/manual2/index.html)

Good luck !

---

### Post by manoj_paul_joseph on 2007-03-19
> **r4ik said:**
> Perhaps this helps ?

[http://www.simonzone.com/software/guarddog/manual2/index.html](http://www.simonzone.com/software/guarddog/manual2/index.html)

Good luck !

Thank you. But I don't think this manual talks about configuring  guarddog to permit access to a port that changes dynamically.

Perhaps guarddog does not have such a feature. Let me check if iptables does.

-Manoj

---

