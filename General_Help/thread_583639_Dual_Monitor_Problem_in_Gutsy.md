---
title: "Dual Monitor Problem in Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by burningbed on 2007-10-20
After upgrading from Feisty to Gutsy my dual monitor setup stopped working.
This bug might be related to:
[http://ubuntuforums.org/showthread.php?t=579861](http://ubuntuforums.org/showthread.php?t=579861)
[http://ubuntuforums.org/showthread.php?t=570231](http://ubuntuforums.org/showthread.php?t=570231)
However it seemed sufficiently different to warrant a separate post.

I'm using an HP Pavilion dv1000 laptop with the intel centrino graphics chipset (i810 driver) and I have an external Lenovo ThinkVision monitor hooked up. The attached xorg.conf worked in Feisty (and Edgy), but now in gutsy, it is no longer usable. The login screen displays fine (in both KDM and GDM) but when KDE or Gnome are loaded, I can only see the background image, but no desktop (however, the startup sound for KDE or Gnome plays as if it was successfully started). Keyboard shortcuts or right clicking with the mouse have no effect. I can load failsafe, start kwin from Konsole and drag windows around both screens as desired. Given this fact and the fact that the same xorg.conf worked in previous versions of Ubuntu, it seems that the desktop environments are somehow involved in the problem. I tried deleting the .kde folder as suggested here [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67985](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67985) , but no luck. Any help would be appreciated as this bug seriously impedes the usability of Gutsy for me.

---

