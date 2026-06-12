---
title: "Ubuntu 19.10, how to get wayland running? Needed for fractional scaling"
date: 2019-10-19
forum: General Help
---

### Post by karl-zylinski on 2019-10-19
Hi, I need Wayland for fractional scaling (the xorg fractional scaling does not work). I had this running nicely in 19.04, but now I can't choose a Wayland session anymore. I tried to hack around a bit in /usr/share/xsessions/ etc, but couldn't get it working. Has anybody got it running? Is there some package I can install that provides the missing Wayland session? (there is no Wayland session to choose anymore in the login screen).

---

### Post by karl-zylinski on 2019-10-19
Ok, so I tried using lightdm instead of gdm3, (just runt apt install lightdm), and from lightdm Ubuntu on Wayland was visible, and I was able to get the fractional scaling working again. Is there some on-purpose-hiding of Wayland going on when using gdm3?

---

