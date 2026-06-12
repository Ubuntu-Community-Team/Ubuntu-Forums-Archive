---
title: "QT apps under XGL lag system"
date: 2007-03-23
forum: General Help
---

### Post by ihatethedekoys on 2007-03-23
QT apps work fine under XGL as long as I am using the beryl window manager. If I switch to metacity or kwin, QT apps cause XGL to use 100% of the cpu, and lags the entire system to the where it is nearly unusable. It lags to the point where I can't click on any toolbar menus without waiting 30 seconds to 1 minute for them to load. As soon as I quit the QT app, everything returns to normal and is fine. Or, if I select the Beryl window manager everything is fine.

So, I would just always use the Beryl window manager except ...

When playing video, even under Beryl Window manager, Kaffeine acts as it does under metacity (laggy, unusable, etc) but if I do the video fullscreen (hiding all the QT elements) there is no lag, and it is fine, but as soon as I move the mouse to the bottom of the screen, showing the controls, etc, it is laggy and my system nearly freezes. It isn't a problem with xine, because gxine works fine in both full screen and windowed mode. So it has to be a QT/XGL problem (at least I think so ... )

Any thoughts on why XGL and QT aren't getting along?

xserver-xgl version 7.0.0.git.20060725-0ubuntu2.1.fglrx.r200 (I have tried the version in the repos, there is no change)
beryl version 0.2.0~0beryl1
fglrx version 8.34.8
linux kernel 2.6.20.1

---

### Post by ihatethedekoys on 2007-03-25
bump.

---

### Post by clawoo on 2007-03-27
> **ihatethedekoys said:**
> 

Any thoughts on why XGL and QT aren't getting along?

xserver-xgl version 7.0.0.git.20060725-0ubuntu2.1.fglrx.r200 (I have tried the version in the repos, there is no change)
beryl version 0.2.0~0beryl1
fglrx version 8.34.8
linux kernel 2.6.20.1

Hi

I have exactly the same problem, qt apps are simply unusable under metacity. When starting up beryl, they're back up and running. Have you found any resolution?

I have:
xserver-xgl version 7.0.0.git.20060725-0ubuntu2.1
beryl 0.1.1-0ubuntu1
kernel 2.6.17-11-generic

---

### Post by ihatethedekoys on 2007-03-29
Bump.

---

### Post by ihatethedekoys on 2007-03-30
I just tried booting into KDE, and it is just as laggy as QT apps are under Gnome. But as soon as I launch the beryl-manager everything is fine.

---

### Post by ihatethedekoys on 2007-10-19
This problem still exists for me under Gutsy. But now video playback in Totem xine gets diagnol tearing and flickering any time something is drawn on top of it, for example the video playback controls at the bottom of the screen, or when I alt+tab.

---

### Post by Anal on 2007-12-13
I solved (Gutsy here), that removing the **xserver-xgl** package.

Now Qt apps start up fast and useable as I was almost forgetting they're able to.

Note that this happens only with Qt3 apps, not with Qt4 ones!

Bye

---

