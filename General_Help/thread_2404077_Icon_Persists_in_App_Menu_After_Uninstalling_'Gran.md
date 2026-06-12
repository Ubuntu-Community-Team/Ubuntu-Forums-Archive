---
title: "Icon Persists in App Menu After Uninstalling 'Granatier' Snap Package"
date: 2018-10-19
forum: General Help
---

### Post by mostafazaman on 2018-10-19
I'm using Ubuntu 18.04. I installed '**Granatier**' (a bomberman-like game) from the snap store. '**kde-frameworks-5**' was also installed in the process. The problem is, Granatier icon wasn't removed from the applications menu after I had uninstalled it by running '**sudo snap remove granatier'**. I also uninstalled 'kde-frameworks-5', suspecting it might have something to do with it. But, no, that ghostly icon is still there. Is there anything I can do to remove it? Thanks in advance. :)

---

### Post by again? on 2018-10-19
Look in **/var/lib/snapd/desktop/applications** for a desktop launcher file.

---

### Post by mostafazaman on 2018-10-20
It worked. Thanks a lot :)

---

