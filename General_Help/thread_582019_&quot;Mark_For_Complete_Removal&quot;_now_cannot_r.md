---
title: "&quot;Mark For Complete Removal&quot; now cannot re-install"
date: 2007-10-19
forum: General Help
---

### Post by Zinger223 on 2007-10-19
Hello!

I have been searching around the internet and the forums for about an hour trying to get my Gutsy Gibbon build to reinstall Network Manager.  I was having problems getting my Broadcom wireless going and thought I would remove the network-manager-gnome, network-manager, as well as wpa_supplicant.  I had two options, so I chose Mark For Complete Removal.  It did its thing and I restarted.  I went into Synaptics Package Manager and found network-manager with a white box next to it.  When I checked to install it, I got an error message to the effect of "package network-manager has no available version".  I have tried terminal commands like sudo aptitude update, sudo aptitude install network-manager and they throw me an error message "no candidate version found for network-manager".  It is also no longer listed under Synaptics.  I have the Ubuntu 7.10 CD in the drive as well as a working network connection.  Please help me get this going again!  I am sure I am missing something and I really want to figure it out rather than re-install.  Thanks so much!

Zinger

---

### Post by mlissner on 2007-10-19
Very strange. Provided this problem isn't solved by reconnecting the Internet into your machine, you could just download the packages from packages.ubuntu.com. 

The easiest way is to put their name in the search bar in Firefox, and then rather than searching Google by pressing enter, press CTRL + Down a couple times until you see the ubuntu logo. Then press enter.

That could do the trick. Once you have them downloaded, just double click them, and they should install. You might run into trouble with dependencies...if so, accept my condolances.

---

