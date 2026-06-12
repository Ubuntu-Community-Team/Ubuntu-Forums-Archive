---
title: "GkrellM says it's using 4GB?!"
date: 2007-05-27
forum: General Help
---

### Post by shen-an-doah on 2007-05-27
So, I've had GkrellM running as it's a nice little system monitor, etc. But when I load up the GNOME system monitor, it says GkrellM is using 4GB of RAM, which is pretty impossible as I only have 512MB and 2GB of swap :confused:

Anyone have any idea what could be happening here?

---

### Post by taurus on 2007-05-27
Probably misconfig in GKrellm.  What does it say about your RAM & swap from this command from a terminal?

Applications -> Accessories -> Terminal
```
free
```

---

### Post by shen-an-doah on 2007-05-27
```
 total       used       free     shared    buffers     cached
Mem:        449440     444244       5196          0       3192      71524
-/+ buffers/cache:     369528      79912
Swap:      2273188     512752    1760436
```

That's what "free" gives me.

Hmmm, how odd, I just restarted GkrellM and it says it's using 800KB now...

---

