---
title: "Compiz + Xinerama + Nvidia?"
date: 2008-05-29
forum: General Help
---

### Post by Schalken on 2008-05-29
How do I enable Compiz with Xinerama on my Nvidia card, with nvidia-glx-new?

Compiz works fine without Xinerama, but as soon as I enable the second screen and try to enable Compiz I get the error "The composite extension is not avaliable." Googling for said error returns a bunch of cases with ATI cards!

---

### Post by kpkeerthi on 2008-05-29
The binary nvidia driver supports multiple displays natively. You need nvidia-settings installed from the repository

1. Install nvidia-settings
```
sudo aptitude install nvidia-settings
```

2. Launch nvidia-settings from command line
```
gksudo nvidia-settings
```

3. Click on 'Detect Displays' and choose the display mode (clone.right-of, left-of, etc)

Optionally if you want to make the change permanent, click on 'Save to Xorg.conf'

---

### Post by Schalken on 2008-05-30
Yup, thats exactly how I'm enabling Xinerama in the first place.

---

### Post by _DD_ on 2008-05-30
With the nvidia drivers you need to enable twinview rather than Xinerama - Xinerama doesn't support the right extensions needed to run Compiz.

---

### Post by Forlong on 2008-05-30
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

There's a guide how to use TwinView

---

### Post by Schalken on 2008-06-01
But TwinView makes my GNOME desktop span both displays - like, the panel goes all across the top spanning both displays and half my bottom panel is visible on the bottom of the taller display (the other half of the panel is hidden in dead area below the shorter display). Fullscreen apps cover both displays as well.

That's not the way it is in either Mac OSX nor Windows, and it's quite ugly. :(

---

### Post by Schalken on 2008-06-03
Aha! If I restart the X server after enabling TwinView, then my window manager grabs display positioning information and correctly puts the gnome-panel and fullscreen windows on just one display. :)

But, just like with real Xinerama, I have to logout and back in when I plug/unplug the external display to achieve this. :(

Oh nVidia, when will you finally support XRandR 1.2?

Thanks for your help.

---

### Post by RAOF on 2008-06-04
> **Schalken said:**
> ...
Oh nVidia, when will you finally support XRandR 1.2?
...

Never, apparently.  They'll possibly/hopefully support XRandR 1.3, which will include support for multi-card.

---

### Post by Schalken on 2008-06-07
Great. And I just found out the reason why Compiz is so choppy on this thing: NVidia's driver enables PowerMizer which underclocks your chip until you give it the load typical of a game. And we can't turn it off either. Not without hacking the xorg.conf or some random module configuration file with an abstraction over the kernel module's understanding of the Windows registry.

Yes! The Windows registry! Nvidia's xorg.conf options are an abstraction of the windows registry!

I bought your hardware and this is the treatment I get?

Nvidia I hate you.

---

