---
title: "Finding/installing software"
date: 2024-04-01
forum: General Help
---

### Post by boowho on 2024-04-01
I've just started using Ubuntu  22.04.4  LTS in "try it" mode.

I've tried finding/installing   both KDE Plasma (I'm not fond of Unity) AND Cairo Dock   

I find many sites that give terminal commands to install these two programs.

Sadly most of the commands throw errors when entered.  I'm a complete NOOB and this is VERY frustrating.

I hate Windows but it's MUCH more user friendly.....   At this point I'm thinking of giving up and returning to Windows;  Linux seems to be "user hostile" to me.

Thanks for reading

Boowho??

---

### Post by Dennis N on 2024-04-01
For Plasma Desktop, you should download and use the installer for Kubuntu, not Ubuntu:

"Kubuntu is an official flavor of the Ubuntu operating system that uses the KDE Plasma Desktop instead of the GNOME desktop environment. As part of the Ubuntu project, Kubuntu uses the same underlying systems."
*--Wikipedia - Kubuntu*

---

### Post by boowho on 2024-04-01
Thank you that will help.   Will it also help with CairoDock??

Boowho

---

### Post by guiverc on 2024-04-01
Ubuntu's Desktop is GNOME, and has been since Ubuntu 17.10 (or the 2017-October release).

Unity (7) desktop is only available if you use the *Ubuntu Unity *ISO, it's now an official flavor, with both *official* and *unofficial* releases seen here - [https://ubuntuunity.org/-](https://ubuntuunity.org/-) but it's probably not Unity you're using/seeing anyway if using Ubuntu 22.04.4 LTS Desktop  (but GNOME).

Official flavors of Ubuntu can be viewed on this page - [https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)

For specific help, the actual commands you tried should be shown, so we know exactly what command you used & can interpret the exact error message for you.

On a *live* system, you usually need to update software lists of the system so it's aware that you're online & thus can download & install packages from the internet (*by default many ISOs will only let you install programs on the media itself until you do this; and those apps are usually already installed!*).  Did you update software lists?  using for example

```

sudo apt update

```

---

### Post by boowho on 2024-04-03
Thanks

---

