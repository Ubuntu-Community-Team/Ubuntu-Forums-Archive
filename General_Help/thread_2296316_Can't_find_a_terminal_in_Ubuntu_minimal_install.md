---
title: "Can't find a terminal in Ubuntu minimal install"
date: 2015-09-25
forum: General Help
---

### Post by tech291083 on 2015-09-25
[URL="https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install_or_core_install.3F"]

[/URL][http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso)

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install_or_core_install.3F](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install_or_core_install.3F)


Freinds,

I have just installed Ubuntu 14.04 Trusty Tahr 32 bit mini iso from the above URL, which I had downloaded last year. As you know, I had to put the installation CD in and connect to the internet to be able to install the base system, which I did. After installation, I restarted my pc and installed GUI by executing the following command

```

sudo apt-get --no-install-recommends install ubuntu-desktop

```

Again, after a reboot I could see the GUI, ut I could not find a terminal, not could I locate a button to shutdown my pc. Can you please help me? Thanks.

---

### Post by nerdtron on 2015-09-25
The terminal application is gnome-terminal probably needs to be installed. Anyway you can always get a TTY terminal from any GUI using the following combination CTRL+ALT+F1 upto F6. And CTRL+ALT+F7 upto F9 brings you back to the GUI.

Why install minimal ISO when you want a GUI?

---

### Post by Bucky Ball on 2015-09-25
I use lxterminal with my mini installs. I also install everything from scratch, NOT ubuntu-desktop, no-recommends or otherwise. Waste of space for my purposes. :)

xfce4 and whatever I need. But it is a production machine, so ... no frills.

If you haven't already I would update/upgrade the machine immediately with this:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

... before installing or doing anything else. These commands won't upgrade 14.04 to a newer release.

---

