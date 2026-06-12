---
title: "Strange Problem with X-Server..."
date: 2007-02-28
forum: General Help
---

### Post by nzk on 2007-02-28
I was having problems with X, so I did dpkg reconfigure xserver-xorg. I rebooted to a horribly broken mess, and changed the driver from mesa to ati. No broken mess, but the resolution is a problem. It's forcing me to run in a terribly low resolution, since if I try to change it to 1920x1200 (my native) it will go all screwy. What do I do? I don't want to have to reformat for my 8th time in half a year because of this!

---

### Post by Stemp on 2007-03-01
Is your monitor detected ? 
In your /etc/X11/xorg.conf what is your monitor section ? 
Mine :
```
Section "Monitor"
        Identifier      "NEC CI LC700"
        Option          "DPMS"
        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 150.0
EndSection

```

---

