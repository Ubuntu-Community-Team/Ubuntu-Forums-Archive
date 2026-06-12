---
title: "cannot import name QTWebkit"
date: 2017-03-24
forum: General Help
---

### Post by Achilles124 on 2017-03-24
I try to load the openlayer plugin in Qgis. It gives me this error:
> cannot import name QTWebkit

I tried to install the latest openlayer plugin from git, but that doesn't work. I get the same error message.

It is related to a previous bug: [http://https://bugs.launchpad.net/ubuntu/+source/qgis/+bug/1649166]("http://https://bugs.launchpad.net/ubuntu/+source/qgis/+bug/1649166")

And I think I have found a possible solution on a Gentoo forum: [http://https://forums.gentoo.org/viewtopic-t-974190.html]("http://https://forums.gentoo.org/viewtopic-t-974190.html")
It says: '> You need to emerge PyQt4 with USE="webkit" turned on'

I really don't know what that means. What file do I have to change?

---

### Post by Achilles124 on 2017-03-26
I think I have found the solution to my problem: [http://hub.qgis.org/issues/15901]("http://hub.qgis.org/issues/15901")

---

