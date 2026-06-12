---
title: "Server - basic gui help"
date: 2006-12-08
forum: General Help
---

### Post by Lord_Freelancer on 2006-12-08
Hello Everyone,

I need a little help, Ubuntu Server with a basic GUI,

firstly i understand about system stuff and how gui affects performance, with that out of the way, i need some help getting a bisic gui installed and working on ubuntu server x64.

i thankyou in advance for some help

---

### Post by taurus on 2006-12-08
Do you want to use Gnome, KDE, XFce4, or fluxbox?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop <-- for Gnome
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install xubuntu-desktop <-- for XFce4
sudo aptitude install fluxbox <-- for fluxbox
```
Just pick one from above and you will have GUI...

---

### Post by Lord_Freelancer on 2006-12-08
omg now that quick service, thank you for souch quick help

---

### Post by yabbadabbadont on 2006-12-08
> **taurus said:**
> Do you want to use Gnome, KDE, XFce4, or fluxbox?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop <-- for Gnome
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install xubuntu-desktop <-- for XFce4
sudo aptitude install fluxbox <-- for fluxbox
```
Just pick one from above and you will have GUI...

I don't think that the fluxbox package in the repositories has the correct dependencies as it doesn't pull in all of the xorg packages that are needed.  (at least it didn't the last time I installed it after a server install)  ((hopefully it has been fixed since then))

---

### Post by taurus on 2006-12-08
Did you use apt-get or aptitude?

---

### Post by yabbadabbadont on 2006-12-08
> **taurus said:**
> Did you use apt-get or aptitude?

Both.  (but on different installations)  I just checked the dependencies and it pulls in some of the xlibs but not x-window-system-core or xserver-xorg.  I guess that's what happens with Universe packages sometimes.  (shrug)

---

