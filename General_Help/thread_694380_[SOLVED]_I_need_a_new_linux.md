---
title: "[SOLVED] I need a new linux"
date: 2008-02-12
forum: General Help
---

### Post by silentabe939 on 2008-02-12
Okay i pose a question to all you linux gurus. Lets say i wanted a verzion of linux that when i install it comes with nothing more than a desktop enviroment and a web browser. where would i find such a thing. the basic idea is that i build the system from that point up installing only what i needed. any ideas?

---

### Post by PeterJS on 2008-02-12
Staying with in the debain family you could install debian from the net install cd, install X, a minimal window manager, and firefox. Working from ubuntu server would be an option if you wanted to stick with ubuntu specifically.

---

### Post by Christmas on 2008-02-12
Yes with Debian you could install only the base system (that's only CLI, no desktop environment) and then install the X Window System, core files from a desktop environment and a login manager:
```
apt-get install x-window-system-core gnome-core gdm
```
Or for KDE
```
apt-get install x-window-system-core kde-core kdm
```
This only brings a window manager and basic applications. You can do the same starting from Ubuntu server, as PeterJS pointed to you. Note that when installing Debian, the desktop environment is selected as the default option, so you'll have to unselect it using SPACE. Leave only Base System selected. Also, when you will install those you'll only be in CLI, so if you have questions get them answered before getting there. However, you can use Lynx as a CLI web browser and Irssi as an IRC client if you got there and need help.

---

### Post by silentabe939 on 2008-02-12
Okay i will check out the ubuntu server distro. I am rather lucky since the initial install will be on my secondary box so i will have my main to get advice. if anyone else has advice let me know. i will check back to let you know how its progressing.

---

