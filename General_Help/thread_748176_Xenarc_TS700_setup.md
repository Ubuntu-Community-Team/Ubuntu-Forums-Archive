---
title: "Xenarc TS700 setup"
date: 2008-04-07
forum: General Help
---

### Post by Mr.Johnny on 2008-04-07
Hi! 

After some time struggling with my xenarc ts700 touchscreen, I found that the current driver does not work with the xorg server in ubuntu, you'll need to ask eeti for the latest beta driver, which still has some flaws, but at least the touch part works now.

Now, my problem is still the resolution, in windows it does 1280x768 fine, but in ubuntu I only have 320x240 or 640x480, I've tried adding the display modes to xorg.conf, but with no sucess, I really don't know what else to do, any suggestions?

Thanks.

---

### Post by Mr.Johnny on 2008-04-08
bump

This doesn't work:

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Modes "640x480" "800x600" "1024x768" "1280x768"
EndSubSection
Defaultdepth 24
EndSection

---

