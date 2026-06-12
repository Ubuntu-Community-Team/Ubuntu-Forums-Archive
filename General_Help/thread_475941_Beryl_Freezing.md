---
title: "Beryl Freezing"
date: 2007-06-16
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2007-06-16
My Beryl Install freezes when a lot of programs are open and Firefox crashes it too. So i'm using another browser but it still freezes. 

My "Device" Section (/etc/X11/zorg.conf)

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Drive          "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    Option         "RandRRotation" "on"
```

Is one of those "Options" causing it? Or what does each of the options do? My card is a GeForce 7300GS and i'm running Feisty.

:D

Thanks :)

---

### Post by s_h_a_d_o_w_s on 2007-06-16
Bump

---

### Post by Luke Davis on 2007-07-23
hi s_h_a_d_o_w_s,

This may apply to your problem so have a look,

[http://www.nvnews.net/vbulletin/showthread.php?t=87918](http://www.nvnews.net/vbulletin/showthread.php?t=87918)

This is as yet unfixed as far as I know. Hope that this helps.

Luke

---

