---
title: "GRLDR Not Found on all Devices"
date: 2007-06-27
forum: General Help
---

### Post by schnauzer93 on 2007-06-27
When I try to boot Ubuntu, I get GRLDR Not Found on all Devices, Press CTRL+ALT+DEL to restart. 

Any ideas?

EDIT: I have to press F6 and type in ***linux acpi=off*** when booting from a Live CD.

---

### Post by ago on 2007-06-27
> **schnauzer93 said:**
> When I try to boot Ubuntu, I get GRLDR Not Found on all Devices, Press CTRL+ALT+DEL to restart. 

Any ideas?

EDIT: I have to press F6 and type in ***linux acpi=off*** when booting from a Live CD.

What wubi version are you using? What is your windows version? Do you have wubildr.* in C:\?

---

### Post by schnauzer93 on 2007-06-27
> **ago said:**
> What wubi version are you using? What is your windows version? Do you have wubildr.* in C:\?
I am using Wubi-7.04-test3, XP Home SP2, and no file by the name of wubildr in my C:\ directory. However, I _do_ have a file named grldr in C:\

---

### Post by ago on 2007-06-27
You should uninstall (move the ISO file somewhere else first), then download Wubi-7.04.01 from the website and save it in the same folder where you have the ISO, then try again.

---

### Post by schnauzer93 on 2007-06-27
OK, now I can start booting, but I get the error message: 

Int 14: CR2 cf800000 err 00000000 EIP c020c384 CS 00000060 flags 00010007
Stack: c00f7d50 c03f129b c0371d8c 00000002 c00f7d59 000f7d50 00000000 00000000

When I try booting from the Live CD, I have to press F6 and type in the command: ***linux acpi=off*** before I continue booting. Is there any way I can boot this way in Wubi?

---

### Post by ago on 2007-06-27
Try to add "acpi=off" to c:\wubi\boot\grub\menu.lst

---

### Post by schnauzer93 on 2007-07-07
Where in the file should I add this line?

---

### Post by tuxcantfly on 2007-07-07
> Where in the file should I add this line?

Towards the end, under all the entries that say "Ubuntu", on the "kernel" line, at the end of the line.

Example:

```
title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro
initrd /wubi/boot/initrd
boot
```

should become:

```
title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro **acpi=off**
initrd /wubi/boot/initrd
boot
```

---

