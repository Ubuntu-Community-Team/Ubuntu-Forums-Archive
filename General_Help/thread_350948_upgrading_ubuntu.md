---
title: "upgrading ubuntu"
date: 2007-02-01
forum: General Help
---

### Post by drumkitcat on 2007-02-01
Hi,

If I install unbuntu 6.06, can I upgrade relatively easily to the latest version?

Or, would it be better to start off with the latest version?

---

### Post by bscbrit on 2007-02-01
An upgrade from the internet is relatively straightforward.  You simply replace each occurrence of 'dapper' with 'edgy' in your repos list (/etc/apt/sources.list) and then use either Synaptic (System->Adminstration->Synaptic Package Manager) or apt-get ('sudo apt-get update' followed by 'sudo apt-get dist-upgrade').

But if you intend to upgrade immediately, you will get a cleaner install by installing fresh from a CD.

---

