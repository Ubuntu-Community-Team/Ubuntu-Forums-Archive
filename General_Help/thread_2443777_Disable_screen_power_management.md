---
title: "Disable screen power management"
date: 2020-05-20
forum: General Help
---

### Post by ilpiero on 2020-05-20
Hello,
I'm using a fresh install of xubuntu 20.04 and I can't seem to turn off the display power management.
No matter what is set in the xfce power manager, the display will blank after 10 minutes.
Screen saver is disabled as well.

Is anyone experiencing the same problem?

Thanks,

Marco

---

### Post by ajgreeny on 2020-05-20
See if you have xfce4-screensaver set to autostart; if I remember correctly the default is for it to just blank the screen.

---

### Post by lvm on 2020-05-20
Add

```
xset -dpms
xset s 0 0
```

to ~/.xinitrc ( of course provided you are using X11)

---

### Post by sisco311 on 2020-05-20
Normally  xfce4-power-manager should use its own DPMS settings and override the Xorg  settings, but in my experience that's not always the case.

You can check the Xorg DPMS settings with:
```
xset q
```
And disable the DPMS features for the current session with:
```
xset -dpms
```

---

### Post by &amp;KyT$0P# on 2020-05-20
I see a similar problem.  I solved it by, in Settings > Screensaver, explicitly turn off "Activate screensaver when computer is idle" before disabling screensaver.

---

### Post by ilpiero on 2020-05-31
Thanks to everybody!
Disabling the DPMS does the job but why the GUI is not working? I tried this on several laptops, all with a fresh install.
Should I report it as a bug?

---

