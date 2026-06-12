---
title: "Firefox &amp; Konqueror 3.5.5 with flashplugin-nonfree freezes"
date: 2006-11-03
forum: General Help
---

### Post by Roque on 2006-11-03
I installed flashplugin-nonfree as explained in the restricted formats page. Both Konqueror (3.5.5) and Firefox freeze temporarily (5 minutes) when entering certain pages (like yahoo groups/mail), youtube, etc.

If I uninstall --purge the plugin, everything works fine again.

Does anyone else have this problem? Any possible fix? Thanks in advance.

---

### Post by LightsOut on 2006-11-04
is this the new flash 9 beta or flash 7. flash 7 shouldnt crash but flash 9 beta crashes more than a blind drunk driver with no hands.

---

### Post by Roque on 2006-11-04
It's from the repos (flash 7). There's no crash: the page eventually loads fine, but it takes more than 5 minutes to do so, and during all that time the browser does not respond nor redraw itself.

---

### Post by Wawalak on 2006-11-14
I switched my default color depth to 24 in xorg.conf and flash is working for me now in both Firefox and Konqueror.

There is another fix that involves adding "export XLIB_SKIP_ARGB_VISUALS=1" to /etc/firefox/firefoxrc, but I don't think that will fix Konqueror.

I found the fix in [this post]("https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911") on Launchpad and also [here]("http://ubuntuforums.org/showthread.php?t=286069&highlight=flash+firefox+crash") in the Ubuntu forums.

---

### Post by Roque on 2006-11-16
Thanks for your help. I already had 24 bpp set in my xorg.conf.

I noticed something: the problem does not happen the first time the plugins are installed in Konqueror (via "Scan fo New Plugins"). Everything runs OK. 

But if I close Konqueror and restart it, then the 5 minutes lag is there.

---

### Post by Roque on 2006-11-21
I just found out that it conflicts somehow with the NVIDIA OpenGL driver: with the flash plugin installed, OpenGL applications work MUCH slower. After removing the plugin, everything works normally again.

---

