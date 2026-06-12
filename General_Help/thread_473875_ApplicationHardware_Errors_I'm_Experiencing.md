---
title: "Application/Hardware Errors I'm Experiencing"
date: 2007-06-14
forum: General Help
---

### Post by DarkDespair5 on 2007-06-14
I'm using the 64-bit version of Ubuntu with the kubuntu-desktop and xubuntu-desktop packages installed.
Ubuntu did not detect my res correctly until I did a dpkg reconfigure and installed the xresprobe. It's a laptop with a NVIDIA graphics card and AMD64ATHLON processor.


Here are the errors:

OpenGL is ridiculously slow.
USB 2.0 devices sporadically fail (sudo modprobe -r ehci_hcd fixes the issue, but now you have 1.1 speeds)
Azureus crashes as it finishes loading.
KTorrent crashes randomly (every hour or so)
SWScanner crashes as soon as I select my wireless device.
kamefu cannot play any type of ROM (even though it detects them correctly)
Ubuntu video players (including VLC) have trouble playing corrupt video. (Even frames without such corruption)
Some fullscreen games lower the resolution of X permanently (reboot fixes it)
Ubuntu spins my external hard drives a LOT more than Windows XP for some reason. (It's audible ;) )
BitTornado light never turns green even when KTorrent and Wined Utorrent report unfirewalledness.
Something seems to prioritize Windows internet traffic over Ubuntu's because on times where both are using the internet heavily, Ubuntu's connection slows to a crawl.


I really have no idea how to submit these as bugs (and maybe these thins just happen to me?)
Any help would be greatly appreciated ^_^
:popcorn:

---

### Post by Damanther on 2007-06-15
What driver do you have installed for that NVIDIA card?

---

