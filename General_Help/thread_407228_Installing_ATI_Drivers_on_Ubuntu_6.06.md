---
title: "Installing ATI Drivers on Ubuntu 6.06"
date: 2007-04-11
forum: General Help
---

### Post by KrackerXIX on 2007-04-11
Okay. So I had tried installing the ATI Drivers through Envy. Envy told me everything installed fine, but obviously it did not. When I ran the glxinfo | grep 'direct'   it told me rendering was off.

> evilxbunny@evilxbunny-laptop:~$ glxinfo | grep 'direct'
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


That is the message I got. So then i go into the Synaptic manager and install the fglrx drivers, and still did not work.   Im using the ATI Radeon Mobility x200m.

This card had also installed fine using Envy on other distros as well, just now its giving me problems. Anyone know what is up?

---

### Post by IcemanV9 on 2007-04-11
There is an excellent [[COLOR="Orange"]**wiki**[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d01742cec183112be090e459b74129606e258f79-2") on ATI video cards.

Look at the contents; link on the word, "Troubleshooting". Follow the instruction.

Good luck, mate.

---

### Post by KrackerXIX on 2007-04-11
okay, i followed his directions to my version, still did not work. my Console still comes up to say > evilxbunny@evilxbunny-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


---

### Post by IcemanV9 on 2007-04-12
So, direct rendering still shows No? From your 1st post, it seems that dri module is not loaded. Make sure "load dri" in the section "Module" is not commented out or missing.

---

### Post by KrackerXIX on 2007-04-12
its there.. and its not commented out.

---

### Post by IcemanV9 on 2007-04-13
I am stumped. :( What about 'radeon' or 'ati' driver? Does direct rendering show Yes with those drivers? FWIW, I have a laptop using 'radeon' driver and it showed "direct rendering: Yes".

---

