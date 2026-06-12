---
title: "steein screen resolution for login screen (dapper)"
date: 2007-03-04
forum: General Help
---

### Post by steve196 on 2007-03-04
How do i set the virtual screen resolution of the login screen to something else, than the maximum?
Thanks!

---

### Post by wxnker on 2007-03-07
I did it this way because my login screen was huge.

**NB**: Remember to **backup** "xorg.conf" before editing.

Kde:
```
sudo kate /etc/X11/xorg.conf
```

Gnome:
```
sudo gedit /etc/X11/xorg.conf
```

In "Section screen" I changed/added this:

```
Section "Screen"
  Identifier "Default Screen"
  Device "nVidia Corporation NV34 [GeForce FX 5500]"
  Monitor "CPD-200GST"
  DefaultDepth 24
  SubSection "Display"
    **[COLOR="Red"]Virtual     1280 1024[/COLOR]**
    depth 24
    modes "1280x1024@75" "1280x960@60" "1280x854" "1280x1024@60" "1152x768@54" "1280x960@75" "1152x864@75" "1400x1050@60" "1024x768@43" "1400x1050@75" "1024x768@60" "1600x1200@65" "1024x768@70" "1600x1200@60" "1024x768@75" "1792x1344@60" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection
```

I did not have the "Virtual" line so I added this above "depth 24"
I set it to 1280 1024 because this is the resolution I use for my desktop.

Hope it helps. :)

---

