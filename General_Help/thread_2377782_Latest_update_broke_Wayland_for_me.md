---
title: "Latest update broke Wayland for me"
date: 2017-11-16
forum: General Help
---

### Post by Rich_S on 2017-11-16
Ran System Updater earlier this morning, rebooted, and when the desktop came up it was all pixelated with gray lines across and flickering like crazy.  Completely unusable.  I was able to logi in under Xorg with no problem though.  I'm running an Intel iGPU.

Packages updated were:

libgl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
libgles2-mesa libwayland-egl1-mesa libxtracker2 mesa-va-drivers
mesa-vdpau-drivers
ubuntu-desktop

Thoughts?

---

### Post by QIII on 2017-11-16
Hello!

Which release are you using?

---

### Post by Rich_S on 2017-11-16
> **QIII said:**
> Hello!

Which release are you using?


Of Wayland?  1.14.0-1

Getting everything from the OIBAF PPA.

BTW, this is an 8700K machine and I have the kernel parameter i915.alpha_support=1 set.

---

### Post by QIII on 2017-11-16
Of Ubuntu.

The PPA may also be at issue.

---

### Post by Rich_S on 2017-11-16
> **QIII said:**
> Of Ubuntu.

The PPA may also be at issue.

17.10.

Only way I could get it to actually use the iGPU as opposed to CPU rendering was with the OIBAF stuff.  It was working fine until the update and reboot this morning.

---

