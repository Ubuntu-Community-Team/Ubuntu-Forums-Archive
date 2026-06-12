---
title: "Broke apt-get"
date: 2007-03-05
forum: General Help
---

### Post by youthforlinux on 2007-03-05
I was trying to install mysql on my edgy desktop, but during the installation after mysql was unpacked, it tried to start mysql, failed, and froze,  I closed the terminal, and then when I tried to re-install some software, it told me to put it ```
sudo dpkg --configure -a
``` to correct the problem.  I tried this, but it just unpacked the mysql database package again and tried to start the mysql server but failed and just did the same thing.  What should I do to fix apt-get to work again.

---

### Post by jimbren on 2007-03-05
Have you tried restarting the upgrade from the beginning?

If you have or if it fails, try the -f switch to fix your broken packages.

```
sudo apt-get -f install
```

jimbo

---

