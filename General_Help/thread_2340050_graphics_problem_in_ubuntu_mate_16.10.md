---
title: "graphics problem in ubuntu mate 16.10"
date: 2016-10-15
forum: General Help
---

### Post by dord2 on 2016-10-15
I have installed ubuntu mate 16.10, after previously working with xubuntu 14.04 without problems and I 
now have some graphics problems.
In firefox or chrome I see a diagonal stripe whenever I scroll.
How to get rid of that?
My hardware info:

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09)
    Subsystem: ASRock Incorporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [1849:0152]
    Kernel driver in use: i915

```
```
OpenGL version string: 3.0 Mesa 12.0.3
```

My system has an intel celeron processor g1610 ivy bridge with hd graphics.

---

### Post by dord2 on 2016-10-15
In case somebody has the same problem,
switching back to Intel sna did the trick.

```
sudo mkdir /etc/X11/xorg.conf.d/
echo -e 'Section "Device"\n Identifier "Card0"\n Driver "Intel"\n Option "AccelMethod" "sna"\nEndSection' | sudo tee /etc/X11/xorg.conf.d/20-intel.conf

```

---

