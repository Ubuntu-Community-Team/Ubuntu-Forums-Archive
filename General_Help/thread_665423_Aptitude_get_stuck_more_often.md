---
title: "Aptitude get stuck more often"
date: 2008-01-12
forum: General Help
---

### Post by lamnk on 2008-01-12
Hi,

Recently i often get stuck when remove software with aptitude. After getting stuck i must kill aptitude in another console. For example:
> Removing libkcal2b ...
Removing libkdepim1a ...
Removing libktnef1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Terminated

or
> (Reading database ... 130271 files and directories currently installed.)
Removing tellico ...
Purging configuration files for tellico ...
Terminated

Anyone has an idea why ?

---

### Post by aysiu on 2008-01-12
I don't know why, but I'm curious--does *apt-get* work? Or does it give you the same *terminated* error message?

---

### Post by kellemes on 2008-01-12
Bug..
Read responses for tips..

[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041]("https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041")

---

