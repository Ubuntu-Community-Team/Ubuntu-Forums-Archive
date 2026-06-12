---
title: "Startup  disk creator not working - Raring 64 bits"
date: 2013-05-01
forum: General Help
---

### Post by kencamargo on 2013-05-01
I just upgraded my system to 13.4, h is working fine  except for the  fact that I cannot get startup disk creator to work, at least not with a flash drive. I set everything up in the main window of the  program, but when I hit the "Make Startup Disk" button the  program aborts saying it couldn't create the disk, and no further explanations. Has anyone else experienced something similar?

Ken

---

### Post by sudodus on 2013-05-01
This is a known bug, but you can install the kde version

```
 sudo apt-get install usb-creator-kde
```

I know it works with the 32 bit systems, probably also with 64 bits. Otherwise there is Unetbootin.

---

### Post by kencamargo on 2013-05-01
Thanks!

---

### Post by Mark Phelps on 2013-05-02
I've used the Universal USB Installer from PendriveLinux.com and found it to work well -- even used it recently with 13.04 when the other installers wouldn't work well.  When you get the menu to choose the Linux version, select the one at the bottom -- the generic entry.

---

