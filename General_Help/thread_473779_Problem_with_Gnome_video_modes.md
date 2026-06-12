---
title: "Problem with Gnome video modes"
date: 2007-06-14
forum: General Help
---

### Post by platofish on 2007-06-14
I am running a fresh install of Ubuntu. The hardware is standard off the shelf stuff. Everything seems to work well except the video display.

My monitor is an Acer AL2216W with native resolution of 1680x1050. When the install completed, the display mode was 1600x1200 which works pretty well. However it would be crisper if it were 1680x1050 so I checked System->Preferences->Screen Resolution to change it. To my surprise only the "standard" resolutions (1600x1200, 1280x1024, 1024x768, 800x600) were available.

I looked through the forums to see if I could find a solution. After reading a few I decided to look at /etc/X11/xorg.conf. I became more confused because 1680x1050 was the first mode listed at all depths.

Can anyone help me figure out what I can change so that Gnome knows about all of the video modes?

---

### Post by Blayde on 2007-06-14
Could you post your xorg.conf here? Perhaps that will help diagnose the problem...

---

