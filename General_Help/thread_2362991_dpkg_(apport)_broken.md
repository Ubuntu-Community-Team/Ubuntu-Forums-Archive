---
title: "dpkg (apport?) broken?"
date: 2017-06-04
forum: General Help
---

### Post by adhdluke on 2017-06-04
When I try to install packages, the terminal returns this:
```
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 apport
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2017-06-05
Did you try reinstalling the 'apport' package, as suggested?

```
sudo apt install --reinstall apport         # 16.04 and newer
sudo apt-get install --reinstall apport     # 14.04
```

---

### Post by adhdluke on 2017-06-05
I didn't know how to do that.. I'm pretty new to Linux. But thanks for the help. It's fixed now.

---

