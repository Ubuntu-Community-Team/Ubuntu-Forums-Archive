---
title: "How to set monitor or refresh rate?"
date: 2008-05-10
forum: General Help
---

### Post by valnar on 2008-05-10
I loaded up Ubuntu 8.04.  I have an ATI card and am using the restricted drivers.

It has my resolution choices for my Hitachi 19" CRT monitor but no refresh rate choice above 60hz. The xorg.conf files look pretty barren - only listing "configured monitor" with no lines of choices.

Is there a new way (or better way) to add my monitor resolutions/rates to Ubuntu 8.04?

Robert

---

### Post by happyhamster on 2008-05-10
If you know the correct horizontal and vertical refreshrates for your monitor, then you can add them manually to xorg.conf. For example, in my xorg.conf it looks like:
```

Section "Monitor"
    Identifier     "Samsung 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

```

Just add the lines for HorizSync and VertRefresh (but with the correct refreshrates for your monitor of course). Don't change anything else though (!).

- To backup xorg.conf:

cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.ori

- To edit xorg.conf:

sudo nano /etc/X11/xorg.conf

- Save = ctrl-o, exit = ctrl-x. Then you'll have to restart X, for example by pressing ctrl-alt-backspace.

- In case things went catastrophically wrong, failsafe-xorg should kick in, or you could always restore the old xorg.conf from the console:

cp /etc/X11/xorg.conf.ori  /etc/X11/xorg.conf



Good luck, and keep us informed.

---

