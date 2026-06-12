---
title: "[SOLVED] removing a package with depencies still needed"
date: 2013-04-07
forum: General Help
---

### Post by kuifje09 on 2013-04-07
How can I remove a package with depency still needed.

When I do   apt-get purge gwibber.*    it will also remove ubuntu-desktop.
However doeing so keeps the desktop running?  But a reinstall also includes gwibber again...

Some say, just leave the package on the system, which is a bit silly. I was thinking of some option like -nodeps.
But apt-get has no  -nodeps option as far I could read about...

Where are the depencies "registred"  , Could I edit those dependencies ? Or any other solution.
( Could remove the binaries and libs.. but that is even more bad behaviour )

---

### Post by oldos2er on 2013-04-07
It's safe to remove ubuntu-desktop, it's a [meta-package]("https://help.ubuntu.com/community/MetaPackages") and nothing will actually be removed by uninstalling it. However if you plan to upgrade to a newer version of Ubuntu, you may need to reinstall it.

---

