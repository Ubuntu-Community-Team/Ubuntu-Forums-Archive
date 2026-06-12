---
title: "webmin help"
date: 2004-11-12
forum: General Help
---

### Post by danip on 2004-11-12
I tried to login into webmin and I got this.  anyone know how to fix this?

---

### Post by TravisNewman on 2004-11-12
I had the same problem. If you've reinstalled or reconfigured webmin, it makes a new certificate. In firefox, go into edit -> preferences -> advanced -> certificates -> manage certificates and get rid of it, and then refresh the page.

---

### Post by danip on 2004-11-12
Ok now iam running into another problem with webmin.  Whenever i try to install a new module it says that it is not supported by my operating system.  If i try to install what there is available via apt-get they never appear in webmin.  anyone having similar problems?

---

