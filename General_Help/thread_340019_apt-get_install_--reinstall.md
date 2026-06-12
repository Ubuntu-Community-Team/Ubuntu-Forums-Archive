---
title: "apt-get install --reinstall"
date: 2007-01-16
forum: General Help
---

### Post by artinla on 2007-01-16
Is there a way to force a package reinstallation and also force the reinstallation of all dependencies?

Thanks,

Art

---

### Post by hal10000 on 2007-01-16
in synaptic right-click on an installed package and select "mark for reinstallation". Then go to "userdefined filters" --->"marked changes" (translated from german) on the left side and do the same with the packages you can see there.

But if you think a package installation may be unclean, then you shold first purge the package and then reinstall.

---

### Post by DerHesse on 2007-01-16
you might be successful with metapackages. I don't know the syntax but you can use synaptic.

---

### Post by jpeddicord on 2007-01-16
It sounds too simple to be true, but if you run a plain apt-get install packagename, it will reinstall it if already installed.

:KS

---

### Post by DerHesse on 2007-01-16
... your dependencies were still allright.

---

### Post by artinla on 2007-01-16
Unfortunately, none of those suggestions will reinstall the dependencies if they are already installed.

---

### Post by DerHesse on 2007-01-16
At least you can check the dependencies in synaptic  (right click, properties.)
and finish your job.

---

