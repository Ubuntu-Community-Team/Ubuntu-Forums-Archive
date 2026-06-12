---
title: "Newly-Installed snap applications not showing up"
date: 2020-12-30
forum: General Help
---

### Post by sniper8752 on 2020-12-30
I recently installed a few applications, such as the store, and a few games.  But when I search for them, they do not appear.  How do I access these programs? I am running Ubuntu 20.04.1 LTS (Focal Fossa) with snap version 2.48+20.04.

---

### Post by vanadium on 2020-12-30
Are you sure you successfully installed these applications? Did you log out and back in as a last rescue? Normally, installed programs should become visible in the overview within seconds, though.

---

### Post by dragonfly41 on 2020-12-30
[Stacer]("https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,%2Drepository%20ppa%3Aoguzhaninan%2Fstacer") offers nice dashboards which show status of installed applications.

---

### Post by TheFu on 2020-12-30
Many programs don't have GUIs and don't come with **.desktop** files, so they don't get added to the menu.  There are probably 1000 programs on our boxes now that don't use a GUI at all. None of those are in the menus.  Depending on the WM or DE, sometimes a logout/login is needed to refresh the menus.

```
snap list
```
Shows which snap packages are installed.  The package name is usually a good thing to try as the program name, but not always.

For example, 
```
$ snap list
Name               Version                     Rev    Tracking       Publisher     Notes
chromium           87.0.4280.88                1424   latest/stable  canonical&#10003;    -
core               16-2.48                     10577  latest/stable  canonical&#10003;    core
core18             20201210                    1944   latest/stable  canonical&#10003;    base
freemind           1.1.0-Beta-2                4      latest/stable  jibel         -
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  145    latest/stable  canonical&#10003;    -
gtk-common-themes  0.1-50-gf7627e4             1514   latest/stable  canonical&#10003;    -
scrcpy             v1.16                       256    latest/stable  sisco311      -
snapd              2.48.1                      10492  latest/stable  canonical&#10003;    snapd
wormhole           0.11.2                      112    latest/stable  snapcrafters  -
```

So, to use freemind, I'd run 'freemind' from any terminal, with my fingers crossed that it will work. That eventually did show the freemind program/GUI after about 30 seconds. Freemind is java, so that is to be expected.  For my needs, java applications are ideal use for a flatpak or snap-package.

In the terminal output, some messages are displayed which should hint at the root issue.  I have a few systems where no snaps ever worked. Not one.  On one system, most snaps work, but not all.

I have no idea why gnome-3-28-1804 is installed. I don't use gnome3 and it is a 20.04 system. I suspect it was pulled in with the core18 dependencies.  That's part of what snaps do.

[https://popey.com/blog/2020/12/snap-tips/](https://popey.com/blog/2020/12/snap-tips/) was in the most recent Weekly Ubuntu Newsletter. It is just some snap commands.

---

