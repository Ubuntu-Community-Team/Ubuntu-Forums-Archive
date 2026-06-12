---
title: "Recompile one module for kernel"
date: 2006-10-16
forum: General Help
---

### Post by nukedathlonman on 2006-10-16
I have a Mitsumi card reader in which the USB Storage kernel module needs a small update to the unusual_dev.h file for it to work properly.  I've built a testing Kernel to confirm that's what the problem is and to test the fix (it works). But it creates a problem I'm unable to correct as the only nVidia module source I can get my hands on is too old to be used with X.  So what I'm wondering is if I can save on a few headaches and simply compile the updated usb_storage module and use that to replace it in a pre-compiled Kernel module?

---

