---
title: "How to adjust &amp; move veiwport?"
date: 2018-02-20
forum: General Help
---

### Post by 1-ben-f on 2018-02-20
I've recently broke my laptop screen (A Mac), resulting in a column of dead pixels along the left side and a row of dead pixels along the bottom of the screen. But the top right area is fine. How could I move the viewport into that area so I can't move my mouse into the dead pixels and the entire Ubuntu DE shows? 

Sorry if this has been asked before. I couldn't find any wording of the question that got results when searching.
```

System:    Host: SystemName Kernel: 4.13.0-32-generic x86_64 bits: 64
           Desktop: Gnome 3.26.2 Distro: Ubuntu 17.10

```
EDIT: Viewport*

---

### Post by cruzer001 on 2018-02-20
Hello

You didn't tell us what OS your running, it makes a difference.

Please post the output of:
```
inxi -S && echo $XDG_SESSION_TYPE
```
Its possible to create a custom resolution just a bit smaller than full screen.

[http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)

---

### Post by 1-ben-f on 2018-02-20
> **cruzer001 said:**
> Hello

You didn't tell us what OS your running, it makes a difference.

Please post the output of:
```
inxi -S && echo $XDG_SESSION_TYPE
```
Its possible to create a custom resolution just a bit smaller than full screen.

[http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)
Yes it is, but if I made a resolution with a different width AND height, then wouldn't it scale the image to only have black bar's on the top&bottom OR left&right?

---

### Post by cruzer001 on 2018-02-20
Yep, thats exactly what would happen.  Its not like rescaling a window within the screen.

Where's the info request?

---

### Post by vasa1 on 2018-02-20
> **cruzer001 said:**
> ..
Where's the info request?

OP edited the first post to include the data you requested.

---

### Post by cruzer001 on 2018-02-20
Thank you vasa1.  I would of never look there :)

@1-ben-f
The second part seems to be missing.
```
echo $XDG_SESSION_TYPE
```

17.10 should default to Wayland and you need to run Xorg (if you use xrandr).

[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

### Post by 1-ben-f on 2018-02-20
> **cruzer001 said:**
> thank you vasa1.  I would of never look there :)

@1-ben-f
the second part seems to be missing.
```
echo $xdg_session_type
```

17.10 should default to wayland and you need to run xorg (if you use xrandr).

[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)


x11

---

### Post by cruzer001 on 2018-02-20
Ok, your good, your on xorg.  Are you going to give xrandr a try?

---

### Post by 1-ben-f on 2018-02-20
> **cruzer001 said:**
> Ok, your good, your on xorg.  Are you going to give xrandr a try?

yeah I am. I can change the height&width without changing the resolution so that there's black borders all around, but can I then move the viewport from the middle of the screen to the top-right?

---

### Post by cruzer001 on 2018-02-20
Short answer, I don't know.

But it wouldn't surprise me if there was a way, probably would take some serious research and would probably be followed with some serious coding.

Maybe someone else will come along with a better solution, give your thread some time.  People read this from all different time zones.

---

