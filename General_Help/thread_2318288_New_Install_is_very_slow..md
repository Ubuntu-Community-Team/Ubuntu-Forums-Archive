---
title: "New Install is very slow."
date: 2016-03-24
forum: General Help
---

### Post by andrew291 on 2016-03-24
Hello.  I've just installed Ubuntu for the first time.  The install seem to go well and I have Ubuntu up and running.  It is very slow.  The transition animations between actions are drawn quite slowly.  How do I fix this?

---

### Post by X-RED_Tech on 2016-03-24
It seems to be some graphical issue, most likely related to graphical drivers but without knowing the hardware specifications it's just guess work.

---

### Post by andrew291 on 2016-03-24
Can Ubuntu source the hardware specs so that I can post them?

---

### Post by andrew291 on 2016-03-24
Older Acer desktop: ASA85-UC521H,  352 INTEL CELERON*D 1GIG RAM

---

### Post by andrew291 on 2016-03-24
Graphics: Gallium 0.4 on llvmpipe (LLVM 3.6, 128bits)

---

### Post by oldfred on 2016-03-24
Full Ubuntu needs newer system with more RAM and newer video chip.

Often better to use Lubuntu or Xubuntu.

With my old laptop 12.04 Unity was so slow as to be unusable, so I installed fall-back or gnome panel. Plus I was used to the old menu system.

 [https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103](http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103)
[https://mail.gnome.org/archives/gnome-announce-list/2013-September/msg00093.html](https://mail.gnome.org/archives/gnome-announce-list/2013-September/msg00093.html)
[http://packages.ubuntu.com/saucy/gnome-session-flashback](http://packages.ubuntu.com/saucy/gnome-session-flashback)
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

---

### Post by X-RED_Tech on 2016-03-24
Current Ubuntu with Unity DE require powerful hardware and preferably more RAM than what you have. Namely it requires powerful 3D capable graphics with proper drivers.
*[COLOR=#000000]Gallium 0.4 on llvmpipe[/COLOR]*[COLOR=#000000] indicates it's using a workaround for the graphics and because of that the bad performance you're complaining about is expected.
What is the graphics card? It probably isn't an integrated Intel which I believe was the default for that model but some addon card. Onboard Intels can use the opensource driver already included in the distro whereas Nvidia or AMD usually require proprietary drivers. You can try the "lspci" command in terminal to get the information about the exact graphics you have.[/COLOR]

---

### Post by andrew291 on 2016-03-24
Thanx... I'll check out the lite distros.

---

### Post by mastablasta on 2016-03-25
> **andrew291 said:**
> Can Ubuntu source the hardware specs so that I can post them?

it can. install **hardinfo **for GUI or use the following terminal commnand:
```

sudo lshw -sanitize
```

---

