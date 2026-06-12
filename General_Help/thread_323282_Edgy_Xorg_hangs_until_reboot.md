---
title: "Edgy Xorg hangs until reboot"
date: 2006-12-21
forum: General Help
---

### Post by lucis on 2006-12-21
When booting up either the Edgy LiveCD or on an installation, X will load, the cursor will appear, then a line of colors will pop up and everything will go blank until I reboot. I have to keep rebooting until the off chance that things will actually work.

Any ideas? :( ](*,)

---

### Post by lucis on 2006-12-29
I'm sorry I can't add any more details, but like I said the cursor appears and the screen goes blank. It won't respond to anything after that.

:(

---

### Post by lucis on 2007-01-01
Nevermind, I fixed it. The Ubuntu splash screen would never appear either and I followed my hunch that that had something to do with it. I booted up on a LiveCD and added a grub menu entry that booted without the "splash" option. Worked. :D

---

