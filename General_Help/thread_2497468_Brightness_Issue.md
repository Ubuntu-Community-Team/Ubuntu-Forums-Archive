---
title: "Brightness Issue"
date: 2024-05-06
forum: General Help
---

### Post by aprilf00lz on 2024-05-06
This happened on both Fedora and Ubuntu, both X11 and Wayland on  Ubuntu. I'm not sure under what conditions it happens, but it has  something to do with my laptop's screen waking up after going black.  Brightness would set itself to max without the brightness slider  displaying this. Interacting with the slider partially fixes it, but the  slider breaks and brightness stops decreasing at around its halfway  point and gets stuck at around 50% no matter how far left I go;  /sys/class/backlight/nvidia_wmi_ec_backlight/brightness and  actual_brightness files change accordingly, but brightness doesn't  change. Restarting fixes it.

---

