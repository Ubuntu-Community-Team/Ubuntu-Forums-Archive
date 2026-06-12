---
title: "memory usage"
date: 2007-11-18
forum: General Help
---

### Post by carteris21 on 2007-11-18
Hello,
     can't understand. If i start my laptop and type free or top(don't start in my own any other programs) my memory usage:
                     total            used            free     shared    buffers     cached
Mem:       1217948    1127224      90724          0      93204     615228
-/+ buffers/cache:     418792     799156
Swap:      1036184        400    1035784

It seems that actually there are no free memory. But System Monitor shows:
User memory: 413MiB of 1.2 GiB 34.8%.

My Ubuntu is quite slow and don't understand how much free memory i have?

---

### Post by monktbd on 2007-11-18
that is just fine.
linux uses a lot of caching so your memory is not taken by applications and what the system monitor tells you is fine.

if your comp runs slow then look at the load average you get with top (on top) or check whether there is an application below that takes a lot of cpu resources or memory.

---

