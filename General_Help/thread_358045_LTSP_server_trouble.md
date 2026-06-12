---
title: "LTSP server trouble"
date: 2007-02-10
forum: General Help
---

### Post by namelessone on 2007-02-10
I'm having trouble booting machines from my Xubuntu ltsp server. I followed the instructions [here]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall").

After using the ltsp-build-client command, I disconnected the server from the internet, hooked it up to a hub and plugged another computer into it to try to get it to boot. I first tried booting with  the network boot option from the cmos menu, but that didn't work, so I made a cd using rom-o-matic, but that didn't work either. It said that it wasn't getting an IP address.

So I guess this means that either the dhcp server isn't working, or I did something really dumb when I plugged these computers into the hub. Can anyone help me?

---

### Post by namelessone on 2007-02-13
Hey! I figured it out! Apparently my server was still trying to get an ip address with dhcp...which doesn't work when it *is* the dhcp server...

problem solved.

---

