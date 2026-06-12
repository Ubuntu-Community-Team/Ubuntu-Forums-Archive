---
title: "Virtualbox error"
date: 2008-05-07
forum: General Help
---

### Post by crimsongrim on 2008-05-07
i am right now getting this error


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 Is there any way to fix this? would appreciate the help, i kind of need it, and fast.

---

### Post by mikerobinson on 2008-05-07
I think the sticky at the top of this section has this mentioned in it.

---

### Post by dreadlord_chris on 2008-05-08
open up a terminal and enter:
```

sudo /etc/init.d/vboxdrv setup

```

That *should* fix it for you.

---

