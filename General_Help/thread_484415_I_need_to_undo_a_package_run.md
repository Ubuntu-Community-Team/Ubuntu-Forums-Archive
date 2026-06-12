---
title: "I need to undo a package run"
date: 2007-06-25
forum: General Help
---

### Post by TeeAhr1 on 2007-06-25
Well, this'll teach me.  Something I just installed depended on the ubuntu-desktop metapackage (I use Kubuntu), so I just walked away from my computer, came back, and saw that it had downloaded and installed 637 packages.  Is there any way for me to undo this (an apt or dpkg logfile would help tremendously, at least)?

-pete

---

### Post by olejorgen on 2007-06-27
You could try to remove ubuntu-desktop and/or the package that caused problems and do ```
sudo apt-get autoremove
```
I have not tried this yet though, and I'm not sure how well it works.

dpkg has a log in /var/log/dpkg.log

---

### Post by notwen on 2007-06-27
Use Synaptic and search for said package(s) you wish to remove.  Right click remove(or remove all) and Synaptic will be kind enough to show you all packages that rely on the package you are wanting to remove and vice versa.  Hope this helps. =]

---

