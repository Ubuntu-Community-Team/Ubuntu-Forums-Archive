---
title: "splash screen not show"
date: 2007-05-04
forum: General Help
---

### Post by ramsesdm on 2007-05-04
Hi, I have Ubuntu Feisty. When I pass the GRUB session I lost the monitor signal until the GDM apear. How can i fix it?

**Configuration**
ASUS P4P800 - VM

---

### Post by thayerw on 2007-05-04
You can have a look at the grub config file to see if the "splash" option is being used...

```
gksudo gedit /boot/grub/menu.lst
```

Somewhere around lines 120-135 you should see your boot menu items... check to make sure it has the splash command as mine does below:

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=00d32749-15e2-494d-8163-cbf86742ce10 ro quiet splash vga=791
```

---

