---
title: "mono 1.1.* ld.so trouble"
date: 2005-04-16
forum: General Help
---

### Post by m87 on 2005-04-16
pride marco # mono
mono: relocation error: mono: symbol __libc_stack_end, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference

this is how.

no apps which require mono can work (duh?) just because the 'mono' interpreter is f*cked.

/me running ubuntu hoary (with breezy repositories) / gcc 4.0, which MIGHT be the reason, but it would be GREAT if i had NOT to use a 3.* gcc version for just one thing that doesn't work!... btw the only thing i could do is to RECOMPILE mono with gcc 4.0... if anyone has other solutions / ideas...

please help me!!

m#

**fixed now... just had to recompile teh whole mono stuff... btw, if you have the same problem... this was my solution**

---

