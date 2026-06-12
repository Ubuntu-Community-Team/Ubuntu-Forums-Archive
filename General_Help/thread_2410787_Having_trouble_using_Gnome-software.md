---
title: "Having trouble using Gnome-software"
date: 2019-01-20
forum: General Help
---

### Post by etrionet on 2019-01-20
Greetings,

I installed Ubuntu MATE 18.04 LTS Bionic Beaver and installing software using Gnome-software is not working properly. At first, I installed Gnome-software using the Software Boutique, but when I searched for packages, only the snaps were shown. I decided to uninstall snap because I wouldn't be using it anyway:
```
sudo apt-get purge snapd
```
Afterwards, Gnome-software didn't find anything (even if I uninstalled [FONT=courier new]gnome-software-plugin-snap[/FONT]). After a reboot, everything worked, except for one thing: most packages didn't have any screenshots, while other packages like [FONT=courier new]youtube-dl[/FONT] or [FONT=courier new]bsdgames[/FONT] didn't appear when searching for them.

They can be installed using [FONT=courier new]apt-get[/FONT], but I would like to be able to install them via the GUI, especially because I like to see some screenshots before installing them.

Am I the only one experiencing these issues?

---

### Post by oldrocker99 on 2019-01-20
Try this, if it isn't already installed.
```
sudo apt iinstall synaptic
```
Synaptic has been my go-to software installer for over 10 years.

---

