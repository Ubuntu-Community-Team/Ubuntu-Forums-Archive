---
title: "problem with GLX"
date: 2005-09-30
forum: General Help
---

### Post by rold50 on 2005-09-30
hi,

when I do glxgears, it works fine I get the gears.
However, when I try to run one of my programs I get an error:

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  23
  Current serial number in output stream:  24


How do I solve this?
I saw from other forums to use nvidia-glx-dev package. However, my graphics card is not nvidia. When I install that, it works fine the program works. When I reboot my computer, then everything screws up. when I do GLXinfo, GLX is not found anymore. So I had to uninstall nvidia-glx.

I also tried doing the readme where it asks to modify the xorg.conf, but the problem is I don't have a device = "nv" because my graphics card is not nvidia.

---

