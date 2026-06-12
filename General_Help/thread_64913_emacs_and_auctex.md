---
title: "emacs and auctex"
date: 2005-09-12
forum: General Help
---

### Post by kakk on 2005-09-12
Hello!
I cannot install auctex on ubuntu. When configuring package, it seems to open an infinite number of /bin/sh -s and make clean processes, and finally I cannot do anything with my computer ](*,)  Has anyone experienced something similar?
When trying to install auctex from source, it also finishes up with infinite loop, though does not increase the number of processes that fast. And the result is, as you may guess, that I cannot get auctex working.

Any help would be really appreciated.

---

### Post by arnieboy on 2005-09-13
[QUOTE=kakk]Hello!
I cannot install auctex on ubuntu. When configuring package, it seems to open an infinite number of /bin/sh -s and make clean processes, and finally I cannot do anything with my computer ](*,)  Has anyone experienced something similar?
When trying to install auctex from source, it also finishes up with infinite loop, though does not increase the number of processes that fast. And the result is, as you may guess, that I cannot get auctex working.

Any help would be really appreciated.[/QUOTE]
tried doing a :
```
sudo apt-get install auctex
``` ?

---

### Post by kakk on 2005-09-13
Well, I used synaptic and tried the apt-get install, both have the same problem. At some stage before completing the installation, it just starts to open up new processes and I usually have to kill about 1000 "make clean" and "/bin/sh" processes. And the same thing happens when I try to compile from source ](*,) 

I really want to use the auctex and it has worked really fine with my previous Mandrake and Debian systems. I also tried to set up the xemacs for that reason but that wasn't succesful enough as well, but that is another story.

---

