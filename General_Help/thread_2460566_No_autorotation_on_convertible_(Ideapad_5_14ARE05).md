---
title: "No autorotation on convertible (Ideapad 5 14ARE05) iio-sensor-proxy &quot;dead&quot;"
date: 2021-04-13
forum: General Help
---

### Post by 0x54 on 2021-04-13
I can't get the autorotation of my laptop to work.
I am running gnome 3.38.3 and the issue is present on Xorg and Wayland.
I have transitioned from ubuntu to xubuntu and back aswell as having installed the latest input-wacom driver from source.

The output of systemctl status iio-sensor-proxy.service is:
```

&#9679; iio-sensor-proxy.service - IIO Sensor Proxy service
     Loaded: loaded (/lib/systemd/system/iio-sensor-proxy.service; static)
     Active: inactive (dead)

```

and monito-sensor gets stuck on "waiting for iio-sensor-proxy to appear"

---

