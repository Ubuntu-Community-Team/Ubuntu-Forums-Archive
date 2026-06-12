---
title: "How I compile xmms for Hardy?"
date: 2008-04-23
forum: General Help
---

### Post by cd-r80 on 2008-04-23
How I compile xmms for Hardy? It complains about GLIB?

---

### Post by gsmanners on 2008-04-24
It probably expects you to have libglib1.2-dev installed. Also, make sure you have:

debhelper, dpatch, autotools-dev, automake, libtool, gettext, libasound2-dev, libaudiofile-dev, libgl1-mesa-dev | xlibmesa-gl-dev, libgtk1.2-dev, libesd0-dev, libice-dev, libmikmod2-dev, libogg-dev, libsm-dev, libvorbis-dev, libx11-dev, libxext-dev, libxi-dev, libxxf86vm-dev, libxml-dev, libssl-dev, sharutils

---

