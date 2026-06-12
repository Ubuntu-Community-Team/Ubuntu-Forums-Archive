---
title: "Discover shows 1 update available although system is up to date"
date: 2018-11-17
forum: General Help
---

### Post by timgood on 2018-11-17
A couple of problems with Plasma 5.14.3 mean that updates in system tray shows 1 update available. CLI shows system up to date. Have tried various combinations of --fix missing and dist-upgrade but problem persists. Also, mouse is set to left handed, but on reboot reverts to right handed while still showing that it is set to left handed! Have to set it back and then set it left handed again. Any ideas? Can live with these, but bloody annoying.

---

### Post by timgood on 2018-11-29
Bump...

---

### Post by timgood on 2018-11-29
This is still the case with 5.14.4
Any  ideas?

---

### Post by vidtek on 2018-11-29
> **timgood said:**
> This is still the case with 5.14.4
Any  ideas?

I had some issues with 4.15 kernels and Kubuntu with the plasma desktop.

I eventually installed UKUU, an Ubuntu graphical kernel update utility.

I then installed kernel 4.19.4, and it solved many niggling issues for me.  

Do not install 4.19.5, that introduced all sorts of problems.

Cheers, Tony.

---

### Post by timgood on 2018-12-01
Thanks Tony. Perhaps I am being dense, but how would installing a newer kernel affect the behaviour of the Plasma desktop settings and Discover?

---

### Post by freemedia2018 on 2018-12-01
> **timgood said:**
> how would installing a newer kernel affect the behaviour of the Plasma desktop settings and Discover?

Plasma desktop uses hardware acceleration, the drivers for which are the kernels job to interact with. If there is a problem with the kernel or the hardware acceleration, a relevant change/fix in the driver or the kernel could help (generally speaking.)

---

### Post by vidtek on 2018-12-01
freemedia answered for me.

cheers both, Tony

---

### Post by timgood on 2018-12-10
Update: the newer kernel makes no difference and I'm still getting these two annoyances. Any other ideas?

---

### Post by vidtek on 2018-12-11
> **timgood said:**
> Update: the newer kernel makes no difference and I'm still getting these two annoyances. Any other ideas?

How are you setting your mouse?  Are you using system settings in KDE?  Or is there a proprietary facility that came with your mouse you use?  If you use xorg.conf there is a setting there, look in all possible locations where the mouse can be changed, check your accessibility settings as well.

I've run out of ideas with the update thing.](*,)]

Cheers Tony

---

### Post by timgood on 2018-12-27
Some more research and a partial answer: the updates issue can be fixed by removing flatpak. Upon logging out and back in this issue disappears.
```
sudo apt-get purge --auto-remove flatpak
```
The mouse issue is a known bug which has been receiving attention for some considerable time and will hopefully be fixed soon.

---

