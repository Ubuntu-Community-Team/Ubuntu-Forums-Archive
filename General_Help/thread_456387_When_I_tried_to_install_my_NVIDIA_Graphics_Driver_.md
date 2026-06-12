---
title: "When I tried to install my NVIDIA Graphics Driver I got a error message."
date: 2007-05-27
forum: General Help
---

### Post by Crafty Kisses on 2007-05-27
I tried to install the NVIDIA Graphics driver through synaptic but when I did i got this error.

> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

Any ideas?

---

### Post by bung33 on 2007-05-28
Did you try editing the configuration file like the error message suggested?

```
sudo gedit /etc/X11/xorg.conf
```

---

