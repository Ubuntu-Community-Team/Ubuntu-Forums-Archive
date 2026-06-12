---
title: "A couple hardy problems with Kiba-Dock, Pidgin, Firefox, Amarok, Skype, etc."
date: 2008-05-12
forum: General Help
---

### Post by KeltGS on 2008-05-12
Okay so I have an Acer 3690-2970 with added ram to 1 GB. It's dual-booted with Vista because I need Photoshop CS3 and Finale 2008. The first thing I did with my machine is to install the b43 driver to my broadcom wireless card. I've also removed Ekiga and Rhythmbox. Since the install of the OS. I've installed gtkboard games (synaptics), gtk-gnutella, skype, sun java 6 web start, ogg convert, sound converter, easy tag, compiz, wine (along with guitar pro 5 in it and powerISO), and amarok. all other have pretty much been installed then uninstalled through add/remove, synaptics, or terminal.

Here are my problems:

1. Guitar Pro 5 does not play sounds.
2. Uninstall of guitar pro 5 leaves a trace in Applications>Wine>Guitar Pro 5
3. Power ISO virtual drive manager doesn't work.
4. Adobe Photoshop CS3 only extracts installer doesn't install (addressed at the wine website?)
5. Pidgin starts and then freezes immediately
6. Skype sound doesn't work (mic), but it works fine on vista.
7. If amorak is open, youtube and other flash players in firefox don't play.
8. if you close amorak and open restart firefox, youtube works BUT amorak ceases to work even if you close firefox.
9. I can't uninstall kiba-dock. I followed the install script here: [http://mathpages.blogspot.com/2008/04/installing-kiba-dock-in-ubuntu-hardy.html](http://mathpages.blogspot.com/2008/04/installing-kiba-dock-in-ubuntu-hardy.html). however, the uninstall script gives me a bunch of "cannot remove, doesn't not exist".  i tried runing some of the commands in the script manually. Here's what the script says:
```
gksudo rm /usr/local/bin/kiba-dock
sudo rm /usr/local/bin/kiba-settings
sudo rm /usr/local/bin/populate-dock.sh
sudo rm -r /usr/local/include/akamaru
sudo rm -r /usr/local/include/kiba-dock
sudo rm -r /usr/local/lib/kiba-dock
sudo rm -r /usr/local/lib/pkgconfig
sudo rm /usr/local/lib/libakamaru.a
sudo rm /usr/local/lib/libakamaru.la
sudo rm /usr/local/lib/libakamaru.so
sudo rm /usr/local/lib/libakamaru.so.0
sudo rm /usr/local/lib/libakamaru.so.0.0
sudo rm /usr/local/lib/libakamaru.so.0.0.0
sudo rm '/usr/local/share/applications/Kiba-Dock.desktop'
sudo rm '/usr/local/share/applications/Kiba-Settings.desktop'
sudo rm -r /usr/local/share/kiba-dock
sudo rm -r /usr/local/share/locale
sudo rm /usr/local/share/pixmaps/kiba-dock.png
sudo rm -r $HOME/kiba
```
10. conky (installed, the uninstalled) won't load on login correctly if it's not in it's own window.

---

### Post by KeltGS on 2008-05-12
Am I allowed to bump?

---

### Post by KeltGS on 2008-05-12
bump

---

### Post by KeltGS on 2008-05-13
please help..

---

### Post by ljungkvist on 2008-06-14
guitar pro can succesfully be replaced with [TuxGuitar]("http://www.tuxguitar.com.ar/home.html").

---

