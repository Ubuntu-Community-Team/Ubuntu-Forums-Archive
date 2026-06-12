---
title: "Software Brightness Adjustment in Wayland"
date: 2017-10-21
forum: General Help
---

### Post by 9072997 on 2017-10-21
I recently upgraded (or more technically did a clean install and moved all of my valuable data) to 17.10. I was previously using a script to adjust my display brightness in software with xrandr (xrandr --output "$output" --brightness $brightness). This does not seem to work now. I suspect it is because of the transition to wayland. Any ideas on how I might adjust the display brightness in software so that I am not blinded trying to use my computer (the LCD does not support back light adjustment. The OSD buttons are entirely inactive, which seems to be an oft-complained about issue with this display)

---

### Post by Xian on 2017-10-22
[COLOR=#000000]xrandr is not compatible with wayland. You have a couple of alternatives:

* Change your DE by choosing Gnome with X11 from the login screen
* Install [/COLOR][brightnessctl]("https://github.com/Hummer12007/brightnessctl")

---

### Post by 9072997 on 2017-11-04
Correct me if I'm wrong, but it dosen't look like brightnessctl would work with an external monitor. Thanks anyway.

---

