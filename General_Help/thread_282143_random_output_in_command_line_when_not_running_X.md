---
title: "random output in command line when not running X"
date: 2006-10-22
forum: General Help
---

### Post by Ay Deverrick on 2006-10-22
Whenever I switch from X server to the 'real' command line (ie, not the Gnome Terminal or KDE Konsole), randomly, even when I'm not logged into the terminal, I'll get random output from my network card.  I know that it's my network card as the output details my ip, mac address, recevied & sent packets, and some other information which is beyond me.  Normally, I'm all for verbose output, but when I'm trying to install my Nvidia drivers so I can use my new video card, it gets really annoying.

Does anyone know what this problem is or how to stop it?

For a network card I'm using a Linksys WMP54G and a compiled version of ndiswrapper.

---

### Post by Ay Deverrick on 2006-10-22
Fixed.

It was the output from Firestarter, and I had to stop the firewall afore shutting down X.

---

