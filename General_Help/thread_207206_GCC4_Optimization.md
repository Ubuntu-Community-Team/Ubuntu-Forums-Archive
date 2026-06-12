---
title: "GCC4 Optimization"
date: 2006-07-01
forum: General Help
---

### Post by Don_DiZzLe on 2006-07-01
Hello everyone,

I've been experimenting with some optimization flags and this is what I got so far:

"-march=athlon64 -02 -pipe -fprofile-generate -fforce-addr -ftree-loop-linear -ftree-loop-im -funswitch-loops -funroll-loops -floop-optimize2 -fprefetch-loop-arrays -ffast-math" 

and then I recompile with the following options:

"-march=athlon64 -02 -pipe -fprofile-use -fforce-addr -ftree-loop-linear -ftree-loop-im -funswitch-loops -floop-optimize2 -fprefetch-loop-arrays -ffast-math"

If someone has better suggestions please let me know, also let me know what u think about my flags.

---

### Post by Don_DiZzLe on 2006-07-01
Sorry for the double thread, can I remove this thread somehow?

---

### Post by matthew on 2006-07-01
[quote=Don_DiZzLe]Sorry for the double thread, can I remove this thread somehow?[/quote]I'll just close this one. If anyone is interested in the subject, please see [http://ubuntuforums.org/showthread.php?p=1202514](http://ubuntuforums.org/showthread.php?p=1202514)

---

