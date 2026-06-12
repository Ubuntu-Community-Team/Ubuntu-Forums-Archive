---
title: "Synaptic shows software updates that &quot;Software Updater&quot; doesn't (Lubuntu 18.04)"
date: 2018-05-17
forum: General Help
---

### Post by gryphus-one on 2018-05-17
Hello, I'm running Lubuntu desktop 18.04 in its 32 bits version and this distro has a menu on the bottom left corner which is very similar to the "Start" menu of Windows. And when you open this menu, you see a series of categories (like Accesories, Graphics, Internet, Office, Sound & Video, System Tools, Preferences...), each one expanding into a submenu where apps classified under that category are shown. Ok, so in "System Tools" you can find several apps, and two of them are "Software Updater" and "Synaptic Package Manager".
I usually use "Software Updater" to update my system but sometimes, just out of simple curiosity, after using Updater I open Synaptic, click on "Reload" and then on "Mark All Upgrades" to check if it finds any updates that Updater has missed, but that has never happened... until just right now: I have installed with "Software Updater" all the updates that this app has shown me, and after that Synaptic has marked a few other packages for upgrading. Surprised, I closed Synaptic without applying any changes, returned to Updater for it to check again for updates but it said that my system was up to date, then I opened Synaptic again and after reloading and marking all upgrades it kept showing some packages for upgrading. I.e, definitely there was a contradiction between these two apps, so here are my questions:
1-Is this normal?
2-One thing that this time has been different from others is that this time, "Software Updater" has not only updated packages already existing in my system, but also installed some new ones. In fact, this time it has requested my password, when usually this app doesn't require it. Could this have something to do with the issue?
3-I applied those upgrades that Synaptic marked, have I done the right thing? In case of contradiction, should I trust Synaptic over "Software Updater" or the other way round?

Thanks in advance.

---

### Post by Dennis N on 2018-05-17
Software Update tool uses phased updates, while Synaptic does not.
[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)
Kernel updates count as new packages, so installing them requires authentication password of administrator. That may be what you are seeing.
The updates you did from Synaptic would eventually be offered in Software Updater.

---

### Post by gryphus-one on 2018-05-17
> **Dennis N said:**
> Software Update tool uses phased updates, while Synaptic does not.
[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)
Kernel updates count as new packages, so installing them requires authentication password of administrator. That may be what you are seeing.
The updates you did from Synaptic would eventually be offered in Software Updater.

Ohh, I didn't know anything about these phased updates, thank you.

---

### Post by missmoondog on 2018-05-19
exactly why i disable the automatic check for updates, (i hate anything automatic) and go straight to synaptic every day. never had a problem updating just using synaptic. most of the time i will go back to software updater and let it check just to find out if i need to restart machine, which i know i will have to if the kernel has been updated, but have seen some other times where a restart is needed. even if i forget to let software updater check for updates, i will still eventually get the pop up to restart machine.

in other words, i always check for updates the exact opposite way you just tried!

---

