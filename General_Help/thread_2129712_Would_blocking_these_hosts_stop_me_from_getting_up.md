---
title: "Would blocking these hosts stop me from getting updates?"
date: 2013-03-27
forum: General Help
---

### Post by Psil0cybin on 2013-03-27
Hey guys quick question, I was wondering if I blocked these hosts within
/etc/hosts

"127.0.0.1       mistletoe.canonical.com127.0.0.1     mulberry.canonical.com"

Would I still be receiving application / software updates through the update manager?
Sorry I am very new :)
My bet is i would as different applications / updates VIA (update manager) depend on various servers, and not on Canonical...correct?
So if I block those hosts, I Should still be able to receive updates and notification through (update manager), just not send out data due to geoip logging. 
and everything is a learning experience.
Thanks in advance
psil0

---

### Post by solarghost on 2013-03-27
127.0.0.1 is always your local IP address. So it seems like somehow your local address was linked to mulberry.canonical.com and mistletoe.canonical.com

I would do this:
```

127.0.0.1	localhost
127.0.0.1  YourPcName

```
But removing 127.0.0.1 from your host file will not stop things from updating.

---

### Post by Psil0cybin on 2013-03-30
Thanks again! Fixed

---

