---
title: "[SOLVED] Firefox running slowly and Flash errors"
date: 2008-06-04
forum: General Help
---

### Post by Goop on 2008-06-04
After updating to Ubuntu 8.04 64-bit, I noticed that there was quite a large decrease in Firefox's performance, often leading it to crash. After trying to browse using Opera instead, I found the same problem occurring. It occurs when loading a page; my whole computer slows to a crawl, stopping Rhythmbox (even though it runs slowly without Rhythmbox open) playing my music until the page has loaded. Also, any windows I have open turn grey because the computer is going so slow that it almost freezes everything.

Since this happens in both Firefox and Opera, I'm going for Flash as the source of the problem. Occasionally, YouTube videos will crash the browser; the page just closes with no explanation and no Talkback pop-up. When running Firefox from the terminal and navigating to Kongregate, this error appeared in the Terminal window:

```
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so [/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
```

From the ELFCLASS64 mention, I guess this is a 64-bit specific problem. Before updating my system, and for a short while afterwards, this problem didn't exist; Flash, Opera and Firefox worked flawlessly. Does anyone know how to fix this problem?

---

### Post by rraj.be on 2008-06-04
The best idea would be to reinstall the flash plugin once again.

I think the installation is corrupted.

and missig of that specific file required may cause this problem.

---

