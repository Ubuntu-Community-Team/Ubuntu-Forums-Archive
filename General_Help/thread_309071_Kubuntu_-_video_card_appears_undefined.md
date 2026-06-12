---
title: "Kubuntu - video card appears undefined"
date: 2006-11-29
forum: General Help
---

### Post by EmperorSquirrels on 2006-11-29
I just did a fresh install of Ubuntu Edgy and installed Kubuntu-Desktop via Synaptic. Problem is, my resolution is much too high for my moniter and I can't change it. And under moniter settings in KDE, it has nv/nv for the graphics adapter. Also, I don't know what happened, but hours ago before I formatted, I did the same thing and once I restarted my resolution seems to be permanently 480x640. It was hell.

Any help? I'm using an Nvidia GeForce 6600.

---

### Post by reclusivemonkey on 2006-11-29
> **EmperorSquirrels said:**
> I just did a fresh install of Ubuntu Edgy and installed Kubuntu-Desktop via Synaptic. Problem is, my resolution is much too high for my moniter and I can't change it. And under moniter settings in KDE, it has nv/nv for the graphics adapter. Also, I don't know what happened, but hours ago before I formatted, I did the same thing and once I restarted my resolution seems to be permanently 480x640. It was hell.

Any help? I'm using an Nvidia GeForce 6600.

You need to install the Nvidia driver. What sort of monitor do you have?

---

### Post by EmperorSquirrels on 2006-11-29
> **reclusivemonkey said:**
> You need to install the Nvidia driver. What sort of monitor do you have?

My monitor is an NEC MultiSynch E700. I've tried installing Nvidia drivers and everything, but it doesn't seem to do anything.

---

### Post by EmperorSquirrels on 2006-11-30
Uh, bump?

---

### Post by reclusivemonkey on 2006-11-30
> **EmperorSquirrels said:**
> Uh, bump?

Did you edit xorg.conf?

Some of us do sleep at night time you know :-P

---

### Post by EmperorSquirrels on 2006-11-30
I don't know how to edit the xorg file. I can't find any place to tell me what SHOULD be there. Here's my "device", "monitor", and "screen" info.

Oh yeah, and this problem is causing me to lose sleep =\ So not too many people get to sleep :(

> Section "Monitor"
    Identifier     "NEC E700"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "NEC E700"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by reclusivemonkey on 2006-11-30
> **EmperorSquirrels said:**
> I don't know how to edit the xorg file. I can't find any place to tell me what SHOULD be there. Here's my "device", "monitor", and "screen" info.

You need to add your monitor's rates; you should be able to find these on the manufacturers site. As an example, here are some sample rates;

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

```

> **EmperorSquirrels said:**
> Oh yeah, and this problem is causing me to lose sleep =\ So not too many people get to sleep :(

I was subtly trying to tell you to be patient when people are helping you. I have a four month old son, so I have other priorities.

---

