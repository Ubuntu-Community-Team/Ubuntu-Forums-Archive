---
title: "Adding a new screen resolution to nVidia-Settings?"
date: 2013-06-22
forum: General Help
---

### Post by Jamie_Edwards on 2013-06-22
Hi guys.

I'm in a little bit of a predicament where I've bought a game that won't work properly with the open source drivers provided by ubuntu. However, the proprietary 310 driver will make it work.

But the resolution is off on the one screen. When I was using the O/S driver, all I'd have to do is the following:
```

-$ xrandr ( To get the initial addresses of each screen let's say VGA-1 and HDMI-1 )

```

Now here's one of the problems
HDMI-1 doesn't have it's native 1920x1080 resolution in nvidia-settings, but does in the O/S driver

I'd then do:
```

-$ xrandr --output HDMI-1 --mode 1920x1080

```

And bob's your uncle, I'm away. But this is not the case with nvidia-settings. If I were to try and add that resolution with the following:

```

-$ cvt 1920 1080
then
-$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
then
-$ xrandr --addmode HDMI-1 "1920x1080_60.00"

```

The last command gives me a BadMatch error and doesn't do anything.

My question ( finally ) is, is there a way that I could add a new resolution to nvidia-settings, assign it to HDMI-1 and then use that new resolution so that I'm able to play the game properly?

Thanks.

Jamie

---

### Post by Jamie_Edwards on 2013-06-23
Anyone?

---

