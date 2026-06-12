---
title: "How to install all packages in apt-cache?"
date: 2007-12-29
forum: General Help
---

### Post by zbog on 2007-12-29
Hello,
I interrupted Synaptic during installation of some packages (>500), how can I resume installation? This happened soon after downloading the selected packages had finished, so I already have all packages I need.
Rephrase: Can I say install all packages in cache, without reselecting them in Synaptic?

Also, I saw in Synaptic I can export the list of selected packages for **downloading** on another computer. I understand this just puts the packages in installation cache, without actually installing them. So again can I install all packages I have in cache?

PS I already killed the zombie dpkg process by using "sudo pkill dpkg".

Thanks in advance!

---

### Post by dagnabit dang doohickey on 2007-12-29
These commands may be of some help:
```
dpkg --list
dpkg --yet-to-unpack
dpkg --audit

```
Check out the dpkg man page for more info.

---

