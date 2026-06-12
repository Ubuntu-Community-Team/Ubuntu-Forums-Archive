---
title: "Some problems with Ubuntu 6.10"
date: 2007-01-27
forum: General Help
---

### Post by Arup on 2007-01-27
I hope there is a workaround for this, Ubuntu by default installs generic kernel on my dual P-III 850 machine, works fine except when you go to install the nvidia-legacy driver for my old Ge Force 256DDR, it would insist on installing 386 kernel which takes away SMP support, if I compile my own kernel and also install its specific headers, the nvidia drivers won't install even with Envy, Currently on my generic kernel only the older Envy 0.73 would install the correct nvidia legacy drivers which seem to be working fine, just have to enable SBA manually.

Any workarounds, from my SuSE 8.1 days, I have always preferred using the latest kernel compiled by myself and optimized for my machine but since I can't install nvidia drivers either from source as well with make install command and it would give me errors telling me unable to find kernel headers even though the headers specific for my kernel is installed.

---

