---
title: "AtiTvout - higher resolution than 1024x768"
date: 2007-10-29
forum: General Help
---

### Post by FredDie3785 on 2007-10-29
I have ATi Radeon 9200 Card, and I followed this tutorial ([http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)) to make tv_out working. Everything goes well, but few days ago I bought a new 19 inch LCD monitor and I want higher resolution than 1024x768 (the highest resolution I could get on my old monitor), but that's the only resolution I'm seeing in the preferences. Any ideas?

---

### Post by ajgreeny on 2007-10-29
Your /etc/X11/xorg.conf file probably needs updating to use a higher resolution than previously.  You can try it manually by adding the appropriate figures into the file a bit like this:-
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        **Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"**
    EndSubSection
EndSection

If that doesn't work enter ```
sudo dpkg-reconfigure -phigh xserver-xorg
```and that may help out and get you where you want to be.

---

