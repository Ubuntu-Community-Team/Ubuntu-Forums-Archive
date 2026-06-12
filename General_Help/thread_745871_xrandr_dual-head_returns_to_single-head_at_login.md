---
title: "xrandr dual-head returns to single-head at login"
date: 2008-04-05
forum: General Help
---

### Post by robbobrob on 2008-04-05
I've moved my home directory onto a USB portable disk, which is another story.  When I mount my home directory on my laptop, which has a full KUbuntu distribution, everything discussed below works fine using just the laptop screen.

My desktop machine has two screens, and was originally an Ubuntu installation, but I've used the  kubuntu-desktop  packge to "convert" it to KUbuntu.  When I start this machine, kdm uses the two screens properly, so my xorg.conf must be close to correct.  When I log in, the screens blank, and just one comes back, then the kubuntu splash screen comes up.  Everything seems to work fine, but with just one screen.  I can run an  xrandr  command to get back to a dual-head setup and that works fine.  When I log out, I go back to one screen (and not the one with  kdm running!).  I've also been getting a console screen with Ctrl-Alt-F1 and this usually works, but Ctrl-Alt-F7 rarely gets me back to X.

Worse, if I use the desktop machine as a mock test user, then the dual-head setup survives the log-in just fine and works as expected.  My home directory began life on my laptop, so it must be that some configuration information there is messing with my dual-head setup on the desktop.  And I think this is further evidence the xorg.conf must be OK.  I've combed thrugh my logs and config files, with no success.  Maybe I've got some old bits of GNOME on the desktop machine causing interference?

Any suggestions on how to fix this, or diagnose it further?  Thanks in advance.

---

