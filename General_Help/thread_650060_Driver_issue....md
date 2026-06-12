---
title: "Driver issue..."
date: 2007-12-25
forum: General Help
---

### Post by IOA on 2007-12-25
Well, I went to go change my drivers for my card (NVIDIA GeForce 8600 GT) so I could support a higher resolution. But this ****** it up and now I can't see ANYTHING. I tried auto-resizing my monitor, which is a 22 inch widescreen, and it didn't work. How the hell do I restore my default drivers? I've screwed around in recovery mode and it hasn't helped me any. 

Please help ASAP, I don't know how long I can be using this computer.

Thanks in advance.


-IOA

---

### Post by taurus on 2007-12-25
Relax.  Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, reboot and see what if it works.

```
shutdown -r now
```

---

### Post by IOA on 2007-12-25
Thanks! It worked!


I'm on my normal computer again ^_^.

---

### Post by taurus on 2007-12-25
Told you to relax.  No needed to get all wired up.

---

