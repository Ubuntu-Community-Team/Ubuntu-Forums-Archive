---
title: "Long startup times after upgrade to 16.04"
date: 2016-07-13
forum: General Help
---

### Post by Edward_Bray on 2016-07-13
A few weeks ago I finally got round to upgrading to 16.04 from a clean install of 15.10. Everything works great, but boot now takes a lot longer than it used to, taking roughly a minute and a half on an SSD instead of the few seconds it used to take. The Windows 10 partition is still just as quick, so I can't think it's anything hardware related. During boot, I also only get a blinking cursor in the top left instead of the splash screen there's meant to be, and a motherboard beep a roughly half way between selecting OS in BURG and the login screen appearing. Shutdown also takes longer than it used to with another beep, but I'm not particularly bothered by that.

Running "systemd-analyze blame" gives different outputs each time. For instance, the longest processes if I do it now are:

```
33.981s apt-daily.service
33.814s colord.service
33.804s lightdm.service
289ms console-setup.service

```

Whereas on one instance in the past I got:

```
34.073s plymouth-quit-wait.service33.941s apt-daily.service
33.941s gpu-manager.service
33.828s snapd.refresh.service
2.397s upower.service
```


Does anyone know what the problem could be? During the update I was given the option to update "/etc/default/rcS" or leave it be. I never knowingly changed this and didn't really know what it was so I decided to update it. Could this be related somehow?

Thanks!

---

