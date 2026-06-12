---
title: "icedtea java does not launch from terminal"
date: 2008-02-18
forum: General Help
---

### Post by Trebaruna on 2008-02-18
Just now I've uninstalled sun-java5 JDK, JRE and their dependencies and installed IcedTea packages (jdk, jre, bin, plugin). Now, however, the command java doesn't work in the terminal (it tells me it can't be found and directs me to installing a number of suggestions). The same goes for javac.
Looking in the /usr/lib/jvm directory reveals IcedTea is installed and fine: ./java in its directory works like it should, and ./javac in its appropriate directory also works as expected.
Eclipse now refuses to start up as well claiming its search in a totally irrelevant location didn't turn up an appropriate VM. Well yes, that's true, but there is a perfectly good one sitting right there!
Running Gutsy x86-64, neatly updated, (re)installed last night.

There must be an easy fix to this, right? Please let me know! :)

---

