---
title: "How to stop a module loading?"
date: 2008-01-29
forum: General Help
---

### Post by nex_neco on 2008-01-29
Ok

I have a intel mobo with a marvell 88se6145 sata controller. 

The module pata_marvell is loading on startup.
Here are the ways I have tried to stop it.

I) add "blacklist pata_marvell" to /etc/modprobe.d/blacklist
II) add file /etc/modprobe.d/00locale with "install pata_marvell /bin/true
III) deleted the pata_marvell.ko file
IV) deleted every reference to the %&¤&%#&/ pata_marvelmodule where ever i have found it.

STILL IT LOADS!!!!

plz help :) thanks

---

### Post by nex_neco on 2008-01-30
sudo dpkg-reconfigure linux-ubuntu-modules-2.6.22-14-server

did the trick :) pata_marvell no longer loads, but can't get the Marvell 6145 controler to work :(

---

