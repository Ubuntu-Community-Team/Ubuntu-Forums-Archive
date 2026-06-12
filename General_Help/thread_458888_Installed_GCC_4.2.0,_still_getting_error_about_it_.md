---
title: "Installed GCC 4.2.0, still getting error about it not being there."
date: 2007-05-30
forum: General Help
---

### Post by AzraelUK on 2007-05-30
I tried to run the demo of darwinia (awesome game, that, check it out!) but I got this error:

```
peter@N00B-PC:~$ cd darwinia-demo2/
peter@N00B-PC:~/darwinia-demo2$ ./darwinia 
.
./lib/darwinia.bin.x86: ./lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
peter@N00B-PC:~/darwinia-demo2$ 

```

So, I changed my sources.list to gutsy, and installed gcc4.2, in the hope that this would fix it. Evidently not, I still get the same error. :/

Any ideas?

---

