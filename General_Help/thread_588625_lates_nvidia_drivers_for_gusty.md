---
title: "lates nvidia drivers for gusty"
date: 2007-10-23
forum: General Help
---

### Post by abistar on 2007-10-23
hello guys, I had a question, could I just download and install the latest drivers from the nvidia site for 7.10 gusty? thanks a lot in advance.

---

### Post by DagMan on 2007-10-23
It depends if that driver will drive your card or not.  If not you may need an older one.  I use the latest drivers from nvidia.  I had to stop the /etc/init.d/linux-restricted-modules-common script from running on boot, but not install the package which meant chmod -x the script or editing it so the first thing it does is exit.  If this breaks other restricted modules you would have to undo it and look at the advanced help to uninstall the nvidia driver and use the ubuntu version.

Installation needs to be done at a console with the xserver not running.
sudo sh NVIDIA*run

---

