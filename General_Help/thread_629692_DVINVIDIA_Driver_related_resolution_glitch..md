---
title: "DVI/NVIDIA Driver related resolution glitch."
date: 2007-12-02
forum: General Help
---

### Post by Asimoth on 2007-12-02
I've got an acer AL2216W monitor (22" widescreen LCD), which supports both DVI and analog inputs, and an NVIDIA GeForce 6600 graphics card.

I booted ubuntu today, to find that my screen resolution was at 640x480. I figured something'd gone wrong with xorg.conf. After a bit of checking, I realized the problem didn't reside there, and so tried switching from digital to analog output. With the analog connector, X server will display at my monitor's native 1680x1050 resolution.

As a side note, when I reconfigured xorg, I used telinit 1, telinit 3 to reload it, and when the NVIDIA driver wasn't active, it was displaying at the monitor's native resolution.

It's been working fine since Feisty was first released, so I'm not sure why it's done this.

---

