---
title: "Dual-head nVidia, non twinview"
date: 2006-11-15
forum: General Help
---

### Post by stubble on 2006-11-15
I have an nvidia 5200 card with one DVI and one VGA port. I have an LCD hooked up to each port.

I have got dual-head working, non-twinview (I don't want a unified desktop, and my DVI monitor is higher res than the VGA one). So that means two device sections, two monitor sections, two screen sections in my xorg.conf. 

So the problem is that the primary monitor is ALWAYS the VGA monitor. It doesn't matter how I reorder them or rename them, dual-head works but the VGA is always the main desktop, login screen, etc. Strangely, if I init 3 and go to text mode, the DVI is the primary.

Any tips?

---

