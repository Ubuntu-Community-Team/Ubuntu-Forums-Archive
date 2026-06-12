---
title: "Downgrade without uninstall?"
date: 2007-01-10
forum: General Help
---

### Post by Adamsmasher23 on 2007-01-10
So I was trying to install WIreshark.  Without thinking I installed libc6 version 2.4.1 from the repository.  However, after I installed it (with GDebi) I opened up SYnaptic and Synaptic said the package was broken.  I told Synaptic to fix it.  Unfortunately, it was a newer version than is in the repository for 6.04.  So now I can't install libc6-dev, since it requires libc6-2.3.6.  Is their any way to install the old version of libc without completely uninstalling it, as uninstalling it would require me to remove tons of packages.

---

### Post by jblebrun on 2007-01-10
> **Adamsmasher23 said:**
> So I was trying to install WIreshark.  Without thinking I installed libc6 version 2.4.1 from the repository.  However, after I installed it (with GDebi) I opened up SYnaptic and Synaptic said the package was broken.  I told Synaptic to fix it.  Unfortunately, it was a newer version than is in the repository for 6.04.  So now I can't install libc6-dev, since it requires libc6-2.3.6.  Is their any way to install the old version of libc without completely uninstalling it, as uninstalling it would require me to remove tons of packages.

Have you tried the force-version option in synaptic, under the package menu?

---

