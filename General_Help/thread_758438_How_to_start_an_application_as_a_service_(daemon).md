---
title: "How to start an application as a service? (daemon?)"
date: 2008-04-18
forum: General Help
---

### Post by dasomen on 2008-04-18
Hello, Newbie here :D,

Does anybody know of a way of starting an app as a service ? What I want to accomplish is to automatically launch firefox at startup... but keep it running no matter what, even if it gets closed or crashes.

Is there any way of doing this?

Thanks in advance,

---

### Post by dcstar on 2008-04-18
> **dasomen said:**
> Hello, Newbie here :D,

Does anybody know of a way of starting an app as a service ? What I want to accomplish is to automatically launch firefox at startup... but keep it running no matter what, even if it gets closed or crashes.

Is there any way of doing this?

Thanks in advance,

You write a script that checks if the process is running, and if not restarts it.

---

### Post by dasomen on 2008-04-18
> **dcstar said:**
> You write a script that checks if the process is running, and if not restarts it.

Thanks dcstar,

Can someone please point me out some example of how to make such script?

---

