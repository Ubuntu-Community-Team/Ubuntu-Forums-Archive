---
title: "Sound in flash works but no picture"
date: 2005-10-22
forum: General Help
---

### Post by starNIX on 2005-10-22
The title explains it.  For some reason,  sound works fine but there is no animation.  I tried flash-nonfree and flash-mozilla from the breezy repos and even tried installing it thru Firefox's plugin installer.  Same problem on all of them.

Any ideas?

---

### Post by RYX on 2005-10-22
If you are missing font animations (so, if fonts are missing completely), try installing the packages gsfonts and gsfonts2 via synaptic - the Flashplayer needs the GhostScript fonts to work - if you installed the binary from macromedia's website you should have gotten that notice after installation ... this was needed in Hoary, don't know if it has changed yet...

---

### Post by starNIX on 2005-10-22
gsfonts and gsfonts-x11 are installed.  Is gv required too?

---

### Post by RYX on 2005-10-22
I'm not sure... Maybe you should try installing the version from macromedia.com - it should inform you about missing dependencies.

---

### Post by starNIX on 2005-10-22
Isn't the one that firefox installs with the plugin finder the macromedia one?

---

### Post by RYX on 2005-10-22
Yes, it should be the same. But I think it is not a FlashPlayer problem, so maybe the installer from macromedia's website (which is an auto-installer in form of a .bin-file) can tell you which additional packages are needed (it told me to install GS fonts when I had a problem with missing fonts) ...

---

### Post by Kirky_D on 2005-10-23
I had the same problem. Do you have adblock extension installed? try disabling it. Worked for me.

---

