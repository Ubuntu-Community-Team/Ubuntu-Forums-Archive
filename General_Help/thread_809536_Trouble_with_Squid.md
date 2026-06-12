---
title: "Trouble with Squid"
date: 2008-05-27
forum: General Help
---

### Post by PcFrk256 on 2008-05-27
I just attempted to install Squid, but when it attempts to start, I get this error message:
```
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE14): Terminated abnormally.
CPU Usage: 0.010 seconds = 0.010 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 4

```

...What do I do?

---

### Post by Monicker on 2008-05-27
You need to edit /etc/squid/squid.conf and set that parameter.

[http://www.visolve.com/squid/squid24s1/admin_parameter.php]("http://www.visolve.com/squid/squid24s1/admin_parameter.php")

---

### Post by JohnPta on 2008-07-05
> **PcFrk256 said:**
> I just attempted to install Squid, but when it attempts to start, I get this error message:
```
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE14): Terminated abnormally.
CPU Usage: 0.010 seconds = 0.010 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 4

```

...What do I do?

I solved most of my problem by reading and working from this website.
[http://sylvarwolflinux.wordpress.com/](http://sylvarwolflinux.wordpress.com/)

---

