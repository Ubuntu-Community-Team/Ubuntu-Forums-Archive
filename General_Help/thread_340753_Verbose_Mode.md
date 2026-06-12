---
title: "Verbose Mode"
date: 2007-01-17
forum: General Help
---

### Post by eppoh on 2007-01-17
Is there any way to switch to "verbose mode' during the boot sequence? With other distros, like Mandrake, hitting esc will do it.

I like to see the services as they load.

---

### Post by taurus on 2007-01-17
Edit /boot/grub/menu.lst and remove the word **quiet** from the entry for kernel.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by eppoh on 2007-01-17
that is pretty permanent. any hotkey combo to do it?

---

### Post by taurus on 2007-01-17
Yeah.  Hit **c** and then modify the entry for the kernel, removing the **quiet**.

---

### Post by nagy barnabas on 2008-01-30
...or just hit alt+F2 any time.

---

