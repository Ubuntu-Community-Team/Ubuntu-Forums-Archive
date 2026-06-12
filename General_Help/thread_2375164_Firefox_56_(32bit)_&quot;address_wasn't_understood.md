---
title: "Firefox 56 (32bit) &quot;address wasn't understood&quot; error"
date: 2017-10-22
forum: General Help
---

### Post by Scott Baker on 2017-10-22
Ok all, here's my issue. I am now running 32 bit Ubuntu MATE 16.04.xx with Firefox 56. Issue is likely with Firefox here. Firefox is giving error 
" the address wasn't understood, Firefox doesn’t know how to open this address, because one of the following protocols (apt) isn’t associated with any program or is not allowed in this context. You might need to install other software to open this address. 
I suspect Firefox is the direct culprit because I've tried my attempts (GETDEB and magnate links through torrent searches) through Opera and Chromium with no issues whatsoever. Trying other Ubuntu installs around my house (Xubuntu 16.04 64bit, Xubuntu 14.04 64bit, MINT w/ Cinnamon 17.2) yields the EXACT same results with Firefox. Firefox is part of the MATE base, so I wasn't allowed to uninstall. In all machines though, I've updated, cleared caches, and checked that all software was installed, to no avail. I've tried online help, and searches here (the forum) with no luck so far. Has anyone figured out how to correct this issue yet?? Thanks in advance, Scott

---

### Post by ajgreeny on 2017-10-22
Do you have the xul-ext-ubufox package installed?

I always remove it preferring to remove the ubuntu extras from FF and keep it closer to the default version, but I think that is what gives the apt execution from FF.

---

