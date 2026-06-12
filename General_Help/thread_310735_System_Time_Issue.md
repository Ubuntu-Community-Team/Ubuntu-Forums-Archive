---
title: "System Time Issue"
date: 2006-12-01
forum: General Help
---

### Post by sargonious on 2006-12-01
I keep having my system time changed by Ubuntu. It's not in sync with it. I remember when I was installing Ubuntu I may have selected that I was on GMT. I think that may be the problem. Every time I switch between XP and Ubuntu it messes up the system and Windows time. How do I fix this so that Windows time and Ubuntu time are synced together with the system time.

---

### Post by NetworkGuy on 2006-12-01
You probably have a problem with UTC..

Edit /etc/default/rcS and change the UTC variable from yes to no

```
 UTC=no
```

---

