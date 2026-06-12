---
title: "Synaptic not opening"
date: 2008-03-28
forum: General Help
---

### Post by 7raTEYdCql on 2008-03-28
I try to open synaptic but i get an error.
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What should i do.
While i was installing something on my computer by mistake i had switched off the computer and therefore that package did not get installed properly.

---

### Post by kpkeerthi on 2008-03-28
Open a terminal and run the below command and follow the instructions. It will make best attempts to fix broken packages if any.

```
sudo dpkg --configure -a
```

---

### Post by 7raTEYdCql on 2008-03-28
Thanks i tried it and i think it is working.

I wanted to know, is there any good ebook or webpage where i can learn all these terminal commands.

---

### Post by erginemr on 2008-03-28
Well, you should check **kpkeerthi**'s signature then, which packs all good sites for a Linux guru wannabe.

---

