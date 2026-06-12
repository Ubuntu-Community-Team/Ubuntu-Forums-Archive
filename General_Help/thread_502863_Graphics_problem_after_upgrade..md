---
title: "Graphics problem after upgrade."
date: 2007-07-17
forum: General Help
---

### Post by Bider on 2007-07-17
I upgraded to feisty fawn, everything seemed okay. But i now have trouble running openGL applications through wine. even though it was not clearly a problem before the upgrade. I get the following errors through wine when trying to run a graphical based application.

> 

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !



I have uninstalled anything that was nvidia-glx related and reinstalled nvidia-glx. and even tried the legacy-glx which seems to support kernel frame buffering through xorg. My card is a nvidia geforce 4.

any solutions?

---

### Post by dragonwings on 2007-07-17
have you tried latest drivers  if not try below

sudo aptitude install nvida-glx-new

sudo apt-get update

then enable restricted driver  and desktop effects but may have to untick them
as woobly windows gave me a plain white non active  termnial window

---

### Post by Bider on 2007-07-17
Found a fix, thx for the help.

---

