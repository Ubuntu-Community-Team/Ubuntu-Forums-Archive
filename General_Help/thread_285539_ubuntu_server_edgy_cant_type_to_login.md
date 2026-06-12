---
title: "ubuntu server edgy: cant type to login"
date: 2006-10-26
forum: General Help
---

### Post by weijie90 on 2006-10-26
hi alll,
i installed ubuntu server 6.10, and i booted into a login prompt, but i cant type anything. i tried all keys, but no letters were displayed. my keyboard is plugged in, and i tried to re-install, in vain.
the installer detected my keyboard layout as us:intl.

please help, thanks!

---

### Post by magicfab on 2006-10-26
Is this a USB keyboard ? If so, you may have to change some options in your BIOS - look for something related to "legacy USB keyboard support". Or you can try installing with a PS/2 keyboard and then switching to USB.

---

### Post by weijie90 on 2006-10-27
nope, its ps/2 which should work fine

---

### Post by weijie90 on 2006-10-27
even the safe mode does not detect my keyboard, and ctrl+alt+F2 does not work. 

actually i just want to avoid bloat in ubuntu. is there a way to do this with the desktop version? thanks

---

### Post by magicfab on 2006-10-27
I am not sure I get this. How can you get through the install if the keyboard is not working ? Have you tried switching keyboards ? Can you access your BIOS ?

---

### Post by weijie90 on 2006-10-27
the keyboard is fine, the installer worked fine.

its a problem with the acpi controller i think:

"i8042.c: Can't read CTR while initialzing i8042"

the numlock, caps, scrollock keys are unresponsive either. acpi=off in grub does not help, except to enable the power button.

thanks!

---

### Post by weijie90 on 2006-10-28
...anybody? =)

---

