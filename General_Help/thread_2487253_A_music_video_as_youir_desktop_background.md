---
title: "A music video as youir desktop background?"
date: 2023-05-29
forum: General Help
---

### Post by jonfisher on 2023-05-29
I was watching Dio sing "Rainbow in the Dark" and someone posted a video of images for desktop that change as song plays - see it here:

[https://www.youtube.com/watch?v=90N8ai0tOtk](https://www.youtube.com/watch?v=90N8ai0tOtk)


Is it possible to do this on Ubuntu 22.x lts 

?

---

### Post by Holger_Gehrke on 2023-05-29
On X11 with mpv and xdotool you can do
```

mpv --wid=$(xdotool search --name Schreibtisch) "video-file"

```
to play a video on the desktop
You will probably have to use another name for the desktop window, "Schreibtisch" is the name on a German XFCE. You can use xwininfo to find out the name.

Don't ask me about how to do it on Wayland.

Holger

---

