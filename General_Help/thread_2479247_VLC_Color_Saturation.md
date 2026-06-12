---
title: "VLC Color Saturation"
date: 2022-09-19
forum: General Help
---

### Post by Shibblet on 2022-09-19
A new issue has popped up out of nowhere...  the color saturation in VLC is WAY overblown.  I have gone through all of the VLC settings to no avail.  And since this problem just came out of nowhere, I don't know if it's a driver issue with Kubuntu, or if it's a VLC problem.

Anyone else having this issue?

---

### Post by #&amp;thj^% on 2022-09-19
> **Shibblet said:**
> A new issue has popped up out of nowhere...  the color saturation in VLC is WAY overblown.  I have gone through all of the VLC settings to no avail.  And since this problem just came out of nowhere, I don't know if it's a driver issue with Kubuntu, or if it's a VLC problem.

Anyone else having this issue?

If hardware is Nvidia then it's possible. I would have bet you would have included more info than that. :(
Here's a brief link, pay attention to the QT portion: [https://wiki.videolan.org/VLC_HowTo/Adjust_image_settings/](https://wiki.videolan.org/VLC_HowTo/Adjust_image_settings/)

---

### Post by Shibblet on 2022-09-19
> **1fallen said:**
> If hardware is Nvidia then it's possible. I would have bet you would have included more info than that. :(

You know, I always forget to include hardware...  It's an AMD Ryzen 5900HX with Vega 8 built in.

---

### Post by #&amp;thj^% on 2022-09-19
> **Shibblet said:**
> You know, I always forget to include hardware...  It's an AMD Ryzen 5900HX with Vega 8 built in.

I haven't gotten my hands on that Chip yet, So at best I would be just guessing on any advice to give you Sir.
Did you investigate that link yet?

---

### Post by Shibblet on 2022-09-19
> **1fallen said:**
> I haven't gotten my hands on that Chip yet, So at best I would be just guessing on any advice to give you Sir.
Did you investigate that link yet?

I did check the link.  Thanks for the quick reply also.

That's the first thing I tried after seeing this problem.  I attempted to make a "saturation" adjustment.  Unfortunately, when I turn on the controls to adjust the saturation, the image goes black, and will not come back on until after I turn off the controls.

This only seems to happen on OpenGL Rendering (VDPAU).  If I switch VLC to X11 rendering, the image seems VERY desaturated.  Reds look orange.  Skin tones start to look grey...

---

### Post by #&amp;thj^% on 2022-09-19
> **Shibblet said:**
>  I attempted to make a "saturation" adjustment.  Unfortunately, when I turn on the controls to adjust the saturation, the image goes black, and will not come back on until after I turn off the controls.

This only seems to happen on OpenGL Rendering (VDPAU).  If I switch VLC to X11 rendering, the image seems VERY desaturated.  Reds look orange.  Skin tones start to look grey...

This sounds like a bad driver or missing "libs" anyway this sounds like a very unpleasant experience.
Is VLC the only player you've tried/used?

---

### Post by Shibblet on 2022-09-19
> **1fallen said:**
> This sounds like a bad driver or missing "libs" anyway this sounds like a very unpleasant experience.
Is VLC the only player you've tried/used?

I tried running mPlayer, and the results seem to be better, but again seem to be too de-saturated.  Give me a few, and I will post some screenshots.

---

