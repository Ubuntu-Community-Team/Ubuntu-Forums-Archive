---
title: "nvidia restricted driver prevents startup"
date: 2007-05-11
forum: General Help
---

### Post by Petergeek on 2007-05-11
I ticked the Restricted Drivers box to enable the nvidia driver and now my PC freezes when Unbuntu 7.04 starts up. My only option is to push the reset button.

I can boot it up in text mode, but how can I remove the offending nvidia driver?

---

### Post by pizzutz on 2007-05-11
```
sudo nano /etc/X11/xorg.conf
```

look for a section like this

```
Section "Device"
Identifier "nVidia Corporation NV34 [GeForce FX 5200]"
Driver "nvidia"
Busid "PCI:3:0:0"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "NoLogo" "True"
EndSection
```


Your identifier, options, busid ect may be different.
change the Driver line to read

Driver "nv"


save and reboot.

---

### Post by Petergeek on 2007-05-11
Thanks. I'll give it a try.

This is better than Microsoft. I'm not used to actually getting a reply!

---

### Post by pizzutz on 2007-05-11
I started using Linux in November.  These forums helped me through many problems. Now that I know what I'm doing, I like to come in here and help out when I know the answer to a question.  That's what makes this community work. :)

There are a lot of helpful people here, most of whom know much more than I do.  I can tell you how to roll your driver back to the default.  Other people may be able to tell you how to get the restricted drivers to work.

---

### Post by Petergeek on 2007-05-12
Thanks for your help. My machine is now up and working again. :KS

---

### Post by mateuszbaranski on 2007-05-12
> **Petergeek said:**
> Thanks for your help. My machine is now up and working again. :KS
But for better performace try to enable nvidia driver anyway. I am having the same problem and looking for solution.

---

