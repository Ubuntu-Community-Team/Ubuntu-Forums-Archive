---
title: "Problems after installing latest kernel"
date: 2005-09-29
forum: General Help
---

### Post by Nasso on 2005-09-29
Hi all!
I just upgraded to the latest kernel, headers etc with synapitc. I dont know much about kernels at all :/
Now my wireless network doesnt work and firefox doesnt even want to start up :( 
i used this tutorial to setup the wifi-card [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

anyone got any ideas? Is it possible to downgrade the kernel to the version i had before? (dont remember what version it was)

edit: When i try to update firefox in synaptic i get this error.
> E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support


---

### Post by Nasso on 2005-09-29
I have tried reinstalling firefox, doesnt help :( Im getting desperate here :( noone got any idea about what might be wrong?

---

### Post by Irony on 2005-09-29
For the firefox problem do a search, for example;
[http://ubuntuforums.org/showthread.php?t=68530&highlight=firefox+1.07](http://ubuntuforums.org/showthread.php?t=68530&highlight=firefox+1.07)
Apparently for Firefox 1.07 the developers change the name so that it is different from Firefox 1.06 which means you have to uninstall mozilla-firefox/firefox or else it gets confused. This will uninstall a few other things (do this via synaptic and it will tell you what it is uninstalling so you can re-install later).

---

