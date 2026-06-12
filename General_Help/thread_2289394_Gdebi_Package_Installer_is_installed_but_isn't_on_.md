---
title: "Gdebi Package Installer is installed but isn't on the start menu"
date: 2015-08-03
forum: General Help
---

### Post by steve169 on 2015-08-03
I'm running Lubuntu Mini 15.04 from a USB drive.

I want to install LXTerminal from the downloaded file **lxde-common-0.99.0.tar.xz**, so I used Lubuntu Software Center to install Gdebi Package Installer.

Lubuntu Software Center says the Gdebi package is installed, but it's nowhere in the start menu.

How do I make it appear in the start menu, and if that can't be done, how to a run it with the "Run" option?

---

### Post by dragonfly41 on 2015-08-03
Although I don't use Lubuntu my GDebi is found under Applications > System Tools > GDebi Package Installer.

p.s. You can also run the command .. sudo gdebi-gtk

---

### Post by Dennis N on 2015-08-03
> **steve169 said:**
> I'm running Lubuntu Mini 15.04 from a USB drive. I want to install LXTerminal from the downloaded file **lxde-common-0.99.0.tar.xz**, so I used Lubuntu Software Center to install Gdebi Package Installer.


Gdebi Package installer only installs .deb files. It won't work with other types.

But, If you have a .deb file, you can right click on it in the file manager, and there should be an option to open with gdebi package installer.

P[313]

---

### Post by Frogs Hair on 2015-08-03
> **lxde-common-0.99.0.tar.xz** Gedbi won't install the package type posted it is for .deb package installation.

---

### Post by howefield on 2015-08-03
> **steve169 said:**
> Lubuntu Software Center says the Gdebi package is installed, but it's nowhere in the start menu.

It usually goes into System Tools.

If not, installing alacarte menu editor should let you add it, if you want to.

---

### Post by steve169 on 2015-08-03
Many thanks to you all.

---

### Post by NathanRodriguez on 2015-08-03
lxde-common-0.99.0.tar.xz is some kind of compressed file, try right-clicking it with file manager to see if it can be opened using Archive Manager.

---

