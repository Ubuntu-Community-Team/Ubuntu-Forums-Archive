---
title: "Setting A Custom Refresh Rate"
date: 2023-03-13
forum: General Help
---

### Post by graystripe on 2023-03-13
I have a 1080p screen capable of 300hz. For some reason the only two refresh rates I can select for it are 300hz and 60hz from both the NVIDIA X server settings and the Gnome display settings. I want to set it to something between there like 120hz or 144hz but I can't figure out how that's done.

I've tried using cvt to generate a modeline that I fed into xrandr, but attempting to add the mode to the display gives me a BadMatch error. Some digging revealed that this is because xrandr no longer plays nicely with NVIDIA kernel drivers. I used the X server settings to generate a xorg.conf file but there's no obvious way to add a custom refresh rate in there. There's simply a range line with the value '60.0 - 300.0'.

Does anyone know how I'd go about setting up a custom refresh rate of, let's say, 1080p @ 120Hz?

---

### Post by MAFoElffen on 2023-03-13
*That is not how things work...*

If you are running Xorg X11, then  open a terminal session and do 
```

xrandr -q

```
It will return the resolutions with the corresponding refresh rates of your display...

When it says 1080p 60 Hz and 1080p 300 Hz, it means just those two refresh rates... Not anything in-between. It is not a "Range" with a lower limit and upper limit. It literally means those two refresh rates. If it shows resolutions with other refresh rates, then you can set it to those... But only the ones listed.

I hope that explanation clarifies things for you to a new understanding of how that works.

---

