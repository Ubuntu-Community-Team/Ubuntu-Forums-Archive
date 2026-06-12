---
title: "Software updates/upgrades"
date: 2008-06-19
forum: General Help
---

### Post by bagm on 2008-06-19
Hi,
  How does Ubuntu handle updates/upgrades of packages related to configuration files?
  Suppose Some package v1.0 has /etc/some.conf (which I customize). Then Some package v1.1 arrives with a modified version of some.conf containing new configuration items. Is the preexisting config file preserved and the new config file discarded? Is there a way to merge these two files?
  Many thanks in advance.

---

### Post by ibuclaw on 2008-06-19
Hello bagm,

As far as I'm aware, the config files in the /etc/ directory are left alone entirely, so you shouldn't worry about any loss of data in the changes you make.

Infact, the only example I can think of where the config file DOES get appended over is the boot config file from when you install a new kernel.
But as long as you don't restructure the file in any way, you should be just fine.

Regards
Iain

---

### Post by bagm on 2008-06-19
And what if I needed to customize new features that come with the newer package? How should I handle this? Looking inside the .deb file? Just guessing...

Many thanks in advance,
Alejandro.

---

