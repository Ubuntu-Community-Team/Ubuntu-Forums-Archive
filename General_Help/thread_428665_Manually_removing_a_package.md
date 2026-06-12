---
title: "Manually removing a package?"
date: 2007-04-30
forum: General Help
---

### Post by yoblin on 2007-04-30
I tried installing the Konika Minolta 2430 DL printer drivers from the website on Feisty. I converted the RPM to a debian package using alien, and when I installed something went wrong. Now I can't use synaptic, dpkg, or aptitude to remove it.

Synaptic gives:

E: The package magicolor2430dl needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and "dpkg --remove magicolor2430dl" gives:

error processing magicolor2430dl (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 magicolor2430dl

How can I manually remove this package? dpkg --remove --force-remove-reinstreq magicolor2430dl just gives me another script error when it tries to uninstall the package and I'm in the same state..

Thanks,

dan

---

### Post by sdide on 2007-04-30
Have you tried 

dpkg -P --force magicolor2430dl

?

---

### Post by yoblin on 2007-04-30
> **sdide said:**
> Have you tried 

dpkg -P --force magicolor2430dl

?

I ended up editing the post-install script that was causing it to fail every time, then running "dpkg -P --force-all magicolor2430dl" got rid of it.

Thanks a bunch.

---

