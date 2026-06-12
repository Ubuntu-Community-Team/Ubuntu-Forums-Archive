---
title: "Inaccessible Startup Menu with wireless keyboard"
date: 2008-07-04
forum: General Help
---

### Post by kkimic on 2008-07-04
Hello everybody,

I have just installed Ubuntu and am surprised of what I have found out already. Everything great apart from one minor thing: I still keep my windows installation since I need it for work, and during startup I cannot select windows since I am using a wireless keyboard (USB connected bundle with mouse) so it does not work till I am under Ubuntu.

Any ideas how to solve this?

Thanks.

---

### Post by funkydan2 on 2008-07-06
You might need to tell your computer's bios to recognise USB keyboards.

Reboot your computer and before the GRUB menu comes up, press whatever key is required to get into your BIOS settings and enable USB keyboards there.  You might need to find a PS/2 keyboard to do this.

---

### Post by jw5801 on 2008-07-06
I had this same problem, a bios setting should fix it. I found that my usb keyboard worked fine in the bios, but the bios surrendered control of it before grub came up, so couldn't be used again until the kernel was booted to take control of it. Setting the bios to allow 'Legacy Support for USB keyboards' or something similar was what was required.

---

### Post by kkimic on 2008-07-06
Thanks, I am going to check it now. However to be 100% clear my keyboard is wireless, and the remote station is connected to the USB for the mouse, and to the PS2 for the keyboard.

Thanks.

---

### Post by funkydan2 on 2008-07-06
Are you sure that's how the connectors work?  It might be worth using either the USB or the PS/2 connector and seeing what happens.

That you're keyboard is wireless shouldn't make any difference - generally RF keyboards appear to the computer to be normal wired keyboards, it's just that the 'wire' is actually radio/light waves going through the air.

---

