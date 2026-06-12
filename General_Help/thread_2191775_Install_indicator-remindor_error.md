---
title: "Install indicator-remindor error"
date: 2013-12-04
forum: General Help
---

### Post by lumaja2 on 2013-12-04
Ubuntu 12.04 precise Installing through terminal it end up with this "Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?" What should I do?

---

### Post by tgalati4 on 2013-12-04
Shut down any other process using the package manager.  You can only run one instance of the package manager at a time.  Software Center, synaptic, aptitude, apt-get, dpkg, are all using the package manager and you can only have one instance running.  That is why there is a lock file.

---

### Post by lumaja2 on 2013-12-05
Thank you, it worked and is installed.  It is in Dash Home but if I clicked does not start, How to start it?

---

