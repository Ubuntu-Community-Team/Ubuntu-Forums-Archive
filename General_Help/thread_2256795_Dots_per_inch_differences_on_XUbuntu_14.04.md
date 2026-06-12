---
title: "Dots per inch differences on X/Ubuntu 14.04"
date: 2014-12-14
forum: General Help
---

### Post by $yl9pAR%t on 2014-12-14
Hi! Could anybody explain me this difference and tell me what can I do, to get the same result on Ubuntu which I've got on Xubuntu?

Hardware:
Nvidia 6150 with proprietary driver 304
Monitor 1440x900

Xubuntu:
```
dxx@lxx:~$ xdpyinfo | grep -B1 dot  dimensions:    1440x900 pixels (411x263 millimeters)
  resolution:    89x87 dots per inch


dxx@lxx:~$ cat /var/log/Xorg.0.log | grep DPI
[    23.946] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
```

Ubuntu:
```
dxx@lxx:~$ xdpyinfo | grep -B1 dot  dimensions:    1440x900 pixels (381x238 millimeters)
  resolution:    96x96 dots per inch


dxx@lxx:~$ cat /var/log/Xorg.0.log | grep DPI
[    23.753] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
```

---

### Post by $yl9pAR%t on 2014-12-19
Not what I wanted, but perhaps for some users a few workarounds in link below will be satisfactory.

[http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi](http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi)

---

