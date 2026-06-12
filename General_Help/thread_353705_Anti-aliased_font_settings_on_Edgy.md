---
title: "Anti-aliased font settings on Edgy"
date: 2007-02-05
forum: General Help
---

### Post by User2323 on 2007-02-05
I have a 1400x1050 LCD display so I like to set the dpi to 120. The default setting in Font Preferences was "Best shapes," and I changed it to "Subpixel smoothing (LCDs)".

This didn't seem to affect the fonts as much as I'd expect, *except* in Firefox. Suddenly the fonts in Firefox looked amazingly smooth. I wish I had taken a screenshot, but the best way to describe them would be almost the same as in Mac OS X. I tried changing the settings but I couldn't get the same type of rendering in the rest of GNOME.

Later, I installed kubuntu-desktop and set KDE to 120 dpi also. I tried using Firefox in KDE and it wasn't as good as in GNOME. Now I'm back in GNOME, and Firefox's font rendering isn't as good anymore, now it's just the same as the rest of GNOME.

Does anyone have any idea what's going on here? I know it seems like I'm just being picky, but good, readable font rendering is very important to me. It's the main thing that kept me from switching away from Windows for a long time.

Ideally I could get the good font rendering in every app, but I'd be happy with just getting it back in Firefox. Thanks.

---

### Post by kerry_s on 2007-02-05
You can add it to /etc/X11/xorg.conf

sudo gedit /etc/X11/xorg.conf

Put it in the> Section "Monitor"

```
    Option         "DPI" "120 x 120"
```

---

### Post by User2323 on 2007-02-10
> **kerry_s said:**
> You can add it to /etc/X11/xorg.conf

sudo gedit /etc/X11/xorg.conf

Put it in the> Section "Monitor"

```
    Option         "DPI" "120 x 120"
```
Thanks kerry_s, but I tried that and it didn't seem to change anything. I think it did improve the font size in gdm though.

---

