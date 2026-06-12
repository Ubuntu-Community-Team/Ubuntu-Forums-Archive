---
title: "Slow graphics"
date: 2006-11-03
forum: General Help
---

### Post by kernco on 2006-11-03
I am running Edgy, and window scrolling and moving is very slow.  I am not running Beryl or anything, it happens in Gnome/metacity, but also in Xubuntu as well.  This didn't happen in Dapper.  I have a VIA k8n890 chipset for my graphics.  Does anyone know what happened in Edgy that would cause this?

---

### Post by library.ninja on 2006-11-03
I had this problem moving up from Dapper as well.  If I remember correctly either my xorg.conf got messed up or my 3rd party drivers (mine was an ATI chipset) got fubar'ed in the upgrade.  I think the standard reconfig of xorg fixed it up:
sudo dpkg-reconfigure -phigh xserver-xorg

As always, backup xorg.conf before doing this

Hope it helps!

---

