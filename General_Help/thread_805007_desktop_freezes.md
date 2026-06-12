---
title: "desktop freezes"
date: 2008-05-23
forum: General Help
---

### Post by werries on 2008-05-23
So i installed Ubuntu hardy heron on a desktop, an XPS Gen 3.
install runs fine, everything boots.
but when i try to get connected to my wireless network, i find that it wont connect. it asks for wep key, i give it, asks it again, i give, and then the whole desktop freezes, cannot do anything, mouse won't even move. the only solution is to hit the power button!

please help? maybe this is a network issue? i cant get any internet to fix it either. (posting using another pc)

---

### Post by werries on 2008-05-23
oh and my network card is
Texas Instruments ACX 111 54Mbps Wireless Interface

---

### Post by werries on 2008-05-24
Ok. so more info. Its gnome, and the standard nm-applet 0.6.6 is the application. upon trying to connect, i check connection information, and its attemtping to use the acx_pci driver, on the wlan0 interface.
upon attempting to connect, gnome/desktop/whatever freezes up completely. cannot move mouse, and it doesnt not respond to ctrl-alt-backspace commands to reset the X server.

I'm sort of new at linux but not entirely, but this completely baffles me. any suggestions? Maybe a way to update w/o internet? Or a bad installation? (I did install from a live usb instead of cd, as a cd would not boot for some reason). Or maybe i need to use a different driver?

EDIT: Is this one of those terrible drivers that require ndiswrapper instead? and if so, any links to setting this up with my wireless card?

---

### Post by Calixte on 2008-05-24
Are you sure it's the wireless card? Does it only freeze when the card is used?

---

### Post by werries on 2008-05-24
so far nothing else has been freezing or delaying whatsoever.
after a lot of googling and search in ubuntu forums, i think it may be that nm-applet .6 doesnt correctly work with the acx driver due to wpa-supplicant. i dont need wpa.
and i cant figure out how to properly downgrade, as the .deb doesnt let me downgrade and says that i have a newer version.

---

