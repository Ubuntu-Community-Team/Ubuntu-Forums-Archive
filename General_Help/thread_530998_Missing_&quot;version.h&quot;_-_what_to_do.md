---
title: "Missing &quot;version.h&quot; - what to do?"
date: 2007-08-21
forum: General Help
---

### Post by MacMagnus on 2007-08-21
I have a "alternative" installation of Ubuntu. I installed a "command line system" from the Feisty-DVD, and after that I have installed tje packages x-window-system-core, fluxbox, fluxconf and build-essential (of the ones I think are of relevance here).

I have also runned "dist-upgrade".

But. When I'm about to compile "alsa-driver-1.0.14", the "./configure" - command tells me there an error, apparently the file "version.h" is missing.

What can I do?

---

### Post by manimal on 2007-08-23
Install the kernel headers package:

```
sudo apt-get install linux-headers-`uname -r`
```

---

