---
title: "Kernel update broke wireless?"
date: 2007-02-14
forum: General Help
---

### Post by HarrisonHopkins on 2007-02-14
Ok, so my old kernel 2.6.17.10 decided to stop starting up all the way when it boots regularly, so I booted into recovery mode, which for some reason worked, updated the kernel to 2.6.17.11, and booted into it fine. Now however, the driver for my wireless card doesn't seem to work. "ndiswrapper -l" says Driver Installed, Device Present. However, Ubuntu says otherwise. Is there anyway I can fix this? I can't go back to the old kernel because it broke, and I don't want to go to Windows because it's just Windows.

Also, is there a way to convert a .dsk file into a .img file?

---

### Post by igknighted on 2007-02-14
> **HarrisonHopkins said:**
> Ok, so my old kernel 2.6.17.10 decided to stop starting up all the way when it boots regularly, so I booted into recovery mode, which for some reason worked, updated the kernel to 2.6.17.11, and booted into it fine. Now however, the driver for my wireless card doesn't seem to work. "ndiswrapper -l" says Driver Installed, Device Present. However, Ubuntu says otherwise. Is there anyway I can fix this? I can't go back to the old kernel because it broke, and I don't want to go to Windows because it's just Windows.

Also, is there a way to convert a .dsk file into a .img file?

This is normal.  Your ndiswrapper module was built for your old kernel.  To get it working again, go back to whatever how-to you used and follow the steps to build the module again.

---

### Post by HarrisonHopkins on 2007-02-14
Ok, thank you. That worked perfectly.

Does anyone know the answer to the other question?

---

