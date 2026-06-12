---
title: "udev rule doesn't run"
date: 2014-11-23
forum: General Help
---

### Post by Lockheed on 2014-11-23
I created a udev rule to run when HDMI is connected/disconnected:
/etc/udev/rules.d/99-hdmi_switch.rules
```
SUBSYSTEM=="drm", ACTION=="change", RUN+="/home/user/bin/video_switch"
```
Now, if I run the command manually, it works. But it does nothing upon HDMI plug/unplug.

What could be amiss here?

---

