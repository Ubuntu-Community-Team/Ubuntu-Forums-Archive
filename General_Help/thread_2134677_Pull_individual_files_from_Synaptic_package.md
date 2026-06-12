---
title: "Pull individual files from Synaptic package?"
date: 2013-04-11
forum: General Help
---

### Post by nessin on 2013-04-11
I need the lircd init script from the synaptic package because I forgot to install Lircd and then remove it before compiling a branch from source, but I can't find any way of pulling a package from synaptic and extracting a single file without installing it.

---

### Post by Vaphell on 2013-04-11
lirc?
download [http://archive.ubuntu.com/ubuntu/pool/universe/l/lirc/lirc_0.9.0-0ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/lirc/lirc_0.9.0-0ubuntu3_amd64.deb)
unpack it (available under right click)
in case xubuntu can't unpack deb archives via gui, try dpkg -x

---

