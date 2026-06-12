---
title: "Why does  Screen Resolution change at start up?"
date: 2007-05-11
forum: General Help
---

### Post by doccpu on 2007-05-11
At grub loading of the kernel i have a 800x600 or better screen but just before it inits the 6 tty's it changes to a grainy 80x25. Where does it set the vga console characteristics?

it will be a nice 80x45 then blam its back to 80x25 then starts the 6 tty's. Where does it change  it?

---

### Post by dcstar on 2007-05-11
> **doccpu said:**
> At grub loading of the kernel i have a 800x600 or better screen but just before it inits the 6 tty's it changes to a grainy 80x25. Where does it set the vga console characteristics?

it will be a nice 80x45 then blam its back to 80x25 then starts the 6 tty's. Where does it change  it?

All my ttys are set by the "vga=xxx" line in my /boot/grub/menu.lst boot string, for instance:

```
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=5b84954a-487b-4af1-a80f-421aa229dce3 ro quiet splash **vga=0x0318**
```

---

### Post by siraf on 2007-05-24
fyi, the numbers after vga corresepond as follows:
```

Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795

```

---

