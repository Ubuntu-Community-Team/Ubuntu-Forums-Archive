---
title: "Sluggish 3D desktop performance even on decent GPU"
date: 2008-07-08
forum: General Help
---

### Post by Velvet Ghost on 2008-07-08
I have freshly installed Ubuntu on a laptop with a NVidia 8600M GT GPU. Directly after the installation a pop up window told me that I needed proprietary graphics drivers and I followed the instructions, which automatically installed the nvidia-glx-new and nvidia-kernel-common packages. Then I manually installed the nvidia-settings package to get the GUI configuration utility, and found that the installed driver version was 169.12. This is not the bleeding-edge version, but rather a stable and recent version that is recommended by NVidia for this chipset. 

However, on enabling desktop effects (desktop right click-> change desktop background -> visual effects -> extra) I find that performance is curiously poor. The minimize / maximize buttons often respond a fraction of a second after they are clicked, the window close & minimize animations often stutter (low framerate), and sometimes if I minimize a window and then immediately maximize it, there is graphic corruption (strange colours) near the top of the window. 

Overall, desktop performance is sluggish. This GPU, although not high-end, is certainly powerful enough to handle these effects smoothly. I was previously running openSUSE 11.0 and everything was smooth there with twice as many effects, enabled manually with compiz-fusion. Any help would be greatly appreciated. This is my first post at the Ubuntu forums!

Thanks in advance.

---

### Post by Velvet Ghost on 2008-07-08
Not a single reply?

---

### Post by Sealbhach on 2008-07-09
Well, you could type

```
top
```

in the terminal, it would show you what's using up your memory.

It might eliminate some suspects.

.

---

