---
title: "screen resolution"
date: 2007-10-26
forum: General Help
---

### Post by vsobhan3 on 2007-10-26
under the screen resolution, the maximum resolution is 800X600. this makes the fonts and pictures look odd. why is there no option of higher resolution like 1024X

how can i get 1024x resolution

---

### Post by jespdj on 2007-10-26
Make sure you install the right video drivers.
Which graphics card does your computer have?

---

### Post by vsobhan3 on 2007-10-26
when i was using windows, my laptop supported 1024X resolution.
when i was using ubuntu older version, i can see 1024X resolution.
but when i upgraded to ubuntu 7. version, there is no 1024x resolution available.

what can i do

---

### Post by Prospero2006 on 2007-10-26
The master config file for resolution is located under

/etc/X11/xorg.conf

It's not always obvious what the trick is in there, but there is definitely something that
can be done. My friend's monitor was stuck at 640x480 for a long time under ubuntu. Finally, I got around to setting the VertRefresh and HorizRefresh options manually in xorg.conf. 
It worked.

You can also type:

```

sudo dpkg-reconfigure xserver-xorg

```
Prospero
[http://www.neisd.net/imak](http://www.neisd.net/imak)

---

### Post by Steve1961 on 2007-10-26
Or just type:

sudo gedit /etc/X11/xorg.conf

add the resolution you want to this section:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


and make sure the correct refresh rates for your screen are in this section:

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 80.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection


Save and close the file then restart x by alt-ctrl-backspace

---

### Post by Qwerty_ on 2007-10-26
I would firstly make sure you had the restricted drivers enabled.

System>Administration>Restricted Drivers Manager.

---

### Post by Drakkor on 2007-10-26
Thanks,Steve, finally got my resolution right !! :)

---

### Post by Steve1961 on 2007-10-26
> **Drakkor said:**
> Thanks,Steve, finally got my resolution right !! :)

Your welcome :)

---

