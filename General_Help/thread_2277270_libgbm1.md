---
title: "libgbm1"
date: 2015-05-07
forum: General Help
---

### Post by mdavis1231 on 2015-05-07
libgbm1 seems to be stuck and not upgradable.  Is there any way to fix this?

---

### Post by cariboo on 2015-05-07
Which version are you using? For package info, check:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by mc4man on 2015-05-07
What do you mean by stuck? 
If on 14.04 there are no recent updates but one may  have 2 libgbm1 packages installed.
On 14.04 or 14.04.1 *image installs * then usually just libgbm1
On 14.04.2 *image installs* then 2, libgbm1 &  libgbm1-lts-utopic In this case both must be installed though only the later's files are actually installed.

this will tell you - 
apt-cache policy libgbm1 libgbm1-lts-utopic

If you went with a fresh 12.04.5 install then mentioning that would be worthwhile.. (or which  12.04.x if not .5
in that case - apt-cache policy libgbm1 libgbm1-lts-trusty
(though 12.04.x may not use both, don't know..

---

