---
title: "Adding resolution for monitor through KVM switch on Ubuntu 22.04.3"
date: 2024-07-24
forum: General Help
---

### Post by thedeyan on 2024-07-24
When using a Dell P2715Q with my machine, I can select a resolution up to 3840x2160. When I connect the monitor through a KVM switch, I can only select up to resolution 1920x1080. I try to add a new resolution via:
```

gtf 2560 1440 59.9
xrandr --newmode "2560x1440_59.90"  311.31  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync
xrandr --addmode HDMI-0 2560x1440_59.90
```

and I get
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  46
  Current serial number in output stream:  47
```

How can I get higher resolution?

---

