---
title: "Modeline Help"
date: 2007-06-28
forum: General Help
---

### Post by trr135 on 2007-06-28
I'm trying to setup a media PC to work with my Samsung 1080p TV. I can't seem to set a custom resolution via the tools provided, but after a little research I think a custom modeline may be the answer. The only problem is after I put the modeline in my xorg.conf I don't know how to use it. Can anyone help me with what to do next?

---

### Post by avik on 2007-06-28
After editing xorg.conf, just restart X.  Press Control-Alt-Backspace, or if you're using the terminal, use:

```
sudo /etc/init.d/gdm restart
```

---

### Post by trr135 on 2007-06-28
I guess maybe I entered the mode line wrong. Here is part of the xorg.conf

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 68.0
    VertRefresh     55.0 - 65.0
    Modeline "1920x1080p" 176.92  1766 2008 2224 2632  992 992 1083 1120 
    Option         "DPMS"
    Option         "IgnoreEdid" "1"
EndSection

Is there away to specify that the "1920x1080p" modeline is the one I want to use?

---

### Post by avik on 2007-06-29
Try the Modeline Generator at [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl").

---

