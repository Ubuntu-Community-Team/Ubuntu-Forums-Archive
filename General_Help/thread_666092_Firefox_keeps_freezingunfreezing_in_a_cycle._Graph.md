---
title: "Firefox keeps freezing/unfreezing in a cycle. Graphics issue?"
date: 2008-01-13
forum: General Help
---

### Post by louiedog on 2008-01-13
I installed Gutsy 32 bit yesterday from a ShipIt CD. I did all of the upgrades and installed a few things in a short period, so I'm not exactly sure when my problem started. When I start Firefox (2.0.0.11) it almost immediately stops responding and turns grey. After a few seconds it comes back to color and then greys out again when it stops responding. Sometimes I can use it for two or three seconds, other times it immediately stops responding when I click on it. I haven't noticed problems with any other applications.

This is with my visual effects set to Normal. If I change the visual effect setting to None, sometimes  Firefox will work just fine after that, but only after my entire system crawls for a few minutes. With the visual effects at normal the rest of the system seems to work just fine. After this problem started I installed the Firefox alpha from the repositories and it works just fine. Right now I'm typing this in the Firefox alpha, and behind this window is Firefox 2 cycling between grey and color.

Because things seem to change when I altar my visual effects I thought this might be a video issue. I'm using an ATI AIW 9700. According to the restricted drivers manager, the ATI graphics driver is enabled and in use. This is an Athlon 64 3000+ system on a mobo with an Nvidia chipset, and 768 RAM. I tried to install Steam with Wine and it doesn't seem to detect that my video hardware as good enough for CS:S, when it certainly is, but I'm not sure if that's a driver issue or a Wine issue. I'm not here for help on that, I'm just including it in case the information is helpful to this problem.

Any ideas on what I should try or do I need to provide more info?

---

### Post by kathryn on 2008-01-13
Hi,

have you tried reinstalling Compiz?

Specifically, use synaptic package manager to reinstall:

compizconfig-settings-manager
emerald
gnome-compiz-manager

Last day or two I've had sudden issues with AWN crashing (perhaps due to Firefox, which was always open at the time).  Even after disabling AWN, the Compiz (visual effects) settings were automatically reverting to Normal (or none).  The problem may re-surface, but for now the re-install seems to have settled things down.  I suspect a recent Ubuntu update may have introduced a bug...

Hope that helps!

---

