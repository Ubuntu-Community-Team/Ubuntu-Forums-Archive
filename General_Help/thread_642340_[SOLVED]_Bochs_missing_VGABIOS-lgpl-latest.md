---
title: "[SOLVED] Bochs missing VGABIOS-lgpl-latest"
date: 2007-12-16
forum: General Help
---

### Post by yang on 2007-12-16
bochs defaults the romimage to 
/usr/share/bochs/VGABIOS-lgpl-latest, but I can't find this file in any package. Any ideas? Thanks in advance.

BTW, the bochs packages seem to be a bit poorly maintained in general. For instance, bochs defaults to use the X plugin, but that is in a separate and non-required Ubuntu package bochs-x, leading to the cryptic error message:

```
dlopen failed for module 'x': file not found
```

---

### Post by kyle.tk on 2008-01-30
I got that same error too. I installed the vgabios package and added this line to my bochsrc ```
vgaromimage: /usr/share/vgabios/vgabios.bin
```

-kyle

---

