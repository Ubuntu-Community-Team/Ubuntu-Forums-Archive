---
title: "help, undo sudo rmmod ehci_hcd"
date: 2007-06-01
forum: General Help
---

### Post by maka on 2007-06-01
hi,
i unloaded this so that my usb2.0 will work in vmware with windows xp

how can i undo this so that I can have my usb2.0 back in ubuntu?

thanks

---

### Post by gerscht on 2007-06-01
```
 sudo modprobe ehci_hcd
```
will do

---

