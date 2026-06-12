---
title: "ACPI: Unable to turn cooling device [c147cdec] 'on'"
date: 2007-06-06
forum: General Help
---

### Post by Huwawa on 2007-06-06
Whenever turn off X and log into the console, I keep getting the following error message:
```
ACPI: Unable to turn cooling device [c147cdec] 'on'
```

But not only that, it appears constantly, bumping away the current output,  and makes getting anything done virtually impossible. Does anyone know how to suppress these error messages, and also to fix this problem?

---

### Post by loathsome on 2007-06-06
Try booting the kernel with **noapic nolapic pci=assign-busses**

Good luck.

---

### Post by Huwawa on 2007-06-06
Thanks, but it didn't work. Got any other suggestions?

---

### Post by Huwawa on 2007-06-07
Bump

---

### Post by tbresson on 2007-06-07
Try booting on a different kernel version. I get the same message after upgrading my kernel to *16

---

