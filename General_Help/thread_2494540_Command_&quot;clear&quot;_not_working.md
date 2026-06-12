---
title: "Command &quot;clear&quot; not working"
date: 2024-01-19
forum: General Help
---

### Post by rikyexe on 2024-01-19
I just installed Ubuntu server 17.10 and tried to run the "clear" command and when I run it I get this error:



Segmentation fault (core dumped)



I tried running it from the physical computer and it works without any problems but when I try to run it from a program like BitVise or PuTTY it gives me this error, do you know how I can solve it?

---

### Post by MAFoElffen on 2024-01-19
Upgrade to a supported release? 

Seriously. Especially for a Server. 17.10 was an interim release and it reached End Of Life back in July 19 2018. That was almost 6 years ago.

Any other fix I could recommend for that, would be wasted, because the Repo's for it are no longer there active.

---

### Post by Rubi1200 on 2024-01-19
It would be irresponsible for anyone here to even suggest a solution when you are running an insecure, unsupported version.

Backup your data and install a recent LTS edition as soon as possible.

---

### Post by rikyexe on 2024-01-19
I would have done it right away but this is the latest version for 32 bit systems

---

### Post by rikyexe on 2024-01-19
can't, this is the latest version that supports 32-bit systems

---

### Post by TheFu on 2024-01-19
> **rikyexe said:**
> can't, this is the latest version that supports 32-bit systems

Not true.  18.04 supports 32-bit and ESM is still available.

---

### Post by QIII on 2024-01-19
Please provide the specs of your system.  Are you sure it is 32 bit?

As a rule, most volunteers here are reticent to provide help for such out-of-date releases.  The Staff discourages the effort to help with unsupported releases -- particularly very old ones, especially interim releases -- for three reasons:

1.  They are insecure and should not be used.  They become vectors for malfeasance by nefarious agents.

2.  There are no updates available, so even the software is out of date.

3.  There may have been details and considerations then that are likely to have been forgotten by now.

ESM my extend the useful life of your system, but bear in mind that even ESM will eventually run out

---

