---
title: "kswapd0 high CPU usage"
date: 2013-08-03
forum: General Help
---

### Post by deanrock2 on 2013-08-03
Hi all,

I have a problem with kswapd0 using too much CPU when my RAM usage is high. The problem is that the computer is constantly freezing when this happens.

Output of free -m command:
```
             total       used       free     shared    buffers     cached
Mem:          7,7G       7,6G       128M         0B       408K       1,6G
-/+ buffers/cache:       6,0G       1,7G
Swap:         7,4G       7,4G         0B

```

As far as I know OS + all of my applications only use memory under -/+ buffer/cache, which in this case is 6 GB, and other 1.6 GB is used as cache, but can be freed if the system needs it. I don't understand why kswapd0 freezes my system when I should still have 1.6 GB of available memory.

Any ideas why this is happening and what can I do (I cannot upgrade RAM because it's laptop and 8 GB is maximum supported)?

---

