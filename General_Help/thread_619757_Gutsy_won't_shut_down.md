---
title: "Gutsy won't shut down"
date: 2007-11-21
forum: General Help
---

### Post by Baasha on 2007-11-21
After the upgrade to 7.10 the shut applet in the panel doesn't work properly.  When I select Shut Down the computer shuts down normally but then restarts.  After it restarts I can shut down permanently by using the options on the log in screen.

How do I fix this?

---

### Post by mpierce on 2007-11-21
I think and this is only a guess that your upgrade is using xserver-glx instead of xserver-xorg as Gutsy ships with Compiz enabled by default. Try removing xserver-glx and I suspect your problem will be solved. 

Hope this helps...

---

### Post by Baasha on 2007-11-22
Ok, but what if I wanted to keep Compiz?

If Gutsy ships with Compiz enabled, which is true for my system, then won't I be messing up other things that assume that Compiz is there?

Not knowing what Compiz was, I checked it out.  I don't play games and am not into fancy 3D displays, but what else would I be missing if I disabled Compiz?

---

### Post by mpierce on 2007-11-22
You'll be missing nothing and can uninstall all the packages with: 
   sudo apt-get remove compiz* && sudo apt-get autoremove && sudo apt-get remove emerald* && sudo apt-get autoremove

This will give you some HD space back. If you want to later, you can reinstall to try compiz if you want. 

Hope this helps...

---

