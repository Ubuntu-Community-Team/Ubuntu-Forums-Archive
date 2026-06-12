---
title: "ASUS NumberPad support"
date: 2024-01-04
forum: General Help
---

### Post by John_Rose on 2024-01-04
Hello,

I have Ubuntu 22.04.03 with Windows 11 in dual boot.

Some smaller ASUS notepads (in my case ASUS Vivobook 14) have no physical NumLock key and no separate NumberPad on the keyboard. The NumberPad is part of the trackpad and is activated under Windows by a virtual ON/OFF key on the trackpad. The trackpad is supported by Ubuntu (although there is an inconsistency for right-click: a sharp right-click often gives left-click while a steady right-click usually works properly), but the NumberPad is not. ASUS says that their NumberPad will only work on the most recent versions of Windows and that they do not provide support for other operating systems.

Could someone advise on how to make the virtual NumberPad work?

Best regards,
John

---

### Post by John_Rose on 2024-01-11
The "Asus touchpad NumberPad driver" is available on [github]("https://github.com/asus-linux-drivers/asus-numberpad-driver/blob/master/README.md"). It provides NumberPad support on top of the standard Ubuntu touchpad support. For me it works fine except for the % key which I have not been able to activate. If problems the developer can be reached at Luká&#353; Drahník <l.drahnik@gmail.com>.

---

### Post by John_Rose on 2024-11-05
The latest version (6.4.0) of the "Asus touchpad NumberPad driver" fixes the % key issue. Please note that the NumberPad function was not working properly (displaying symbols instead of numbers) on some earlier versions of the driver for Ubuntu installations using the Wayland compositor to manage communications with the display server. This is also now fixed, and I strongly recommend this application.

Please also note that in NumberPad mode, full depression of a number key or a strong click will emulate Touchpad selection functions (emulation of right-click in the case of the two lower right keys (+ and =) and of left-click for other keys). This is intended behaviour, but in NumberPad mode one should get used to not tapping too hard on the number keys unless Touchpad emulation is sought.

---

