---
title: "Resolution/Refresh not saving"
date: 2007-02-09
forum: General Help
---

### Post by Inhumane on 2007-02-09
I have properly installed nVidia drivers from nVidia.com.
Whenever I change my resolution to my monitors native res of 1440x900@75Mhz, it works, but after a restart it keeps reverting back to 1152x864@auto (I think 60 mhz). Is there a way of stopping this from happening?

---

### Post by taurus on 2007-02-10
Did you make the change in /etc/X11/xorg.conf?

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Inhumane on 2007-02-10
> **taurus said:**
> Did you make the change in /etc/X11/xorg.conf?

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

Where would I make that change? This is what I have:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480""
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

```

---

### Post by detectiveinspekta on 2007-03-01
I also have the exact problem.

---

### Post by CocoAUS on 2007-03-01
Um...perhaps you should change the "1440x1440" values to "1440x900".

Hope that helps.

---

### Post by detectiveinspekta on 2007-03-01
I was too lazy to understand what that screen section was for.

So I fixed mine just by adding the resolution to the start of the Modes. From what I assume you can use different resolutions to different color depth. So I assumed that the first resolution is the default.
What I don't understand is that nvidia-settings says color depth is 32bbp, now where is this in the xorg.conf?

---

