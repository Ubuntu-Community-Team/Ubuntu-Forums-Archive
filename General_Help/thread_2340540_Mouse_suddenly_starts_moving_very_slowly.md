---
title: "Mouse suddenly starts moving very slowly"
date: 2016-10-19
forum: General Help
---

### Post by redbiertje on 2016-10-19
Goodday folks,

I was hoping you could help me with a little problem. I'm currently on Ubuntu 14.04, and I sometimes have the issue that after a little while my mouse suddenly starts moving very slowly. It also moves a bit unsmooth. I can't seem to find any event that causes it, so it appears to start very randomly. If I reboot my PC everything is fine again, and my mouse is working without any problems. Does any of you happen to have an idea on how to fix it?

Thank you very much in advance,

Cheers,

Red

---

### Post by Zero_Bytes on 2016-10-19
I experience the same thing when I transfer large files from a usb flash drive, if that's the case, remove it and do```
sudo modprobe ehci_hcd
```

---

