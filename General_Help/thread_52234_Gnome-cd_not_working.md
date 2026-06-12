---
title: "Gnome-cd not working"
date: 2005-07-27
forum: General Help
---

### Post by feloc on 2005-07-27
When I insert a cd, it finds all available information using CDDB but it doesn't play the cd at all. It just stops. Grip, XMMS etc plays the cds very well.

I tried to re-install the packages with no luck. What should I do?

---

### Post by danns on 2005-08-16
This is a bit late but I am having the same issues too and I believe I know what the problem is on my end.

Are you using Gnome?   If not, then chances are esd is not running and if esd is not running you will not be able to play cd's from the gnome-cd player or totem.  You can start esd if you are in gnome or if in gnome and have disabled the sound server startup (re-enable it I guess); at that point those apps seem to work fine.

I'd like to know how to get those apps to use straight alsa, not esd.

---

