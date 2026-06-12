---
title: "what is GDMgreeter and how can I disable it?"
date: 2007-12-10
forum: General Help
---

### Post by popophobia on 2007-12-10
Ok, here are my bootchart from Dec 01st. Notice the extra time (almost twice as much). I don't recall what I tweaked in Dec 01, but I'm sure it extend my boot time a lot. I figure that GDMgreeter have something to do with this. It seems that GDMgreeter access harddrive for almost 20 second (it only shown on the second chart, not on the first).

So, what is GDM Greeter and how can I disable that? Please let me know. Thanks.

BEFORE (fast)
[http://bayimg.com/LAiLmAabb](http://bayimg.com/LAiLmAabb)

AFTER (SLOOOOOOW)
[http://bayimg.com/laiLNAABB](http://bayimg.com/laiLNAABB)

---

### Post by Anduu on 2007-12-11
GDMGreeter is the login screen.....

Have you recently changed it to a more graphically intense one with a face browser ?

That could explain the extra boot time.

---

### Post by popophobia on 2007-12-11
> **Anduu said:**
> GDMGreeter is the login screen.....

Have you recently changed it to a more graphically intense one with a face browser ?

That could explain the extra boot time.

I found out. It's the readahead code line. Seems like it move the reading time from post loging to pre login. :(

---

