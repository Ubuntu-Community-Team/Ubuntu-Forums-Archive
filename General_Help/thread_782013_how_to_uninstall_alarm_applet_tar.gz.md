---
title: "how to uninstall alarm applet tar.gz?"
date: 2008-05-04
forum: General Help
---

### Post by cheeseman557 on 2008-05-04
Hi!

How do I uninstall version 1.2 of alarm applet? The page is here: [http://alarm-clock.pseudoberries.com/](http://alarm-clock.pseudoberries.com/). Thanks!

---

### Post by Patb on 2008-05-04
Cheeseman, it depends on the package.  To uninstall a package which has been installed from source (eg *.tar.gz) you can sometimes go to the install directory (where you issued the install command "sudo make install") and then:
```
sudo make uninstall
```
Cheers, Pat.

---

