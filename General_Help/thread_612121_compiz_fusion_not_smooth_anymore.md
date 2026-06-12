---
title: "compiz fusion not smooth anymore"
date: 2007-11-13
forum: General Help
---

### Post by mckechan on 2007-11-13
I have a nvidia7600GT. I've been messing around for days now trying to get dual tv out with my monitor. In the process of editing xorg.conf I think compiz fusion has messed up.

All the effects are there but if I drag a window it flickers and the edge of the 3D cube flickers.

I attach my xorg.conf. Any idea?

---

### Post by overdrank on 2007-11-14
> **mckechan said:**
> I have a nvidia7600GT. I've been messing around for days now trying to get dual tv out with my monitor. In the process of editing xorg.conf I think compiz fusion has messed up.

All the effects are there but if I drag a window it flickers and the edge of the 3D cube flickers.

I attach my xorg.conf. Any idea?

HI and the only thing I can see that might be missing is 
  Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
Either under the screen section or the device section. I just checked mine and did not have them either and I added them and I could tell the difference. Good luck!
Edit and also you may want to use the nvidia settings to add you tv monitor. gksudo nvidia-settings

---

