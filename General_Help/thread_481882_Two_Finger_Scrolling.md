---
title: "Two Finger Scrolling"
date: 2007-06-23
forum: General Help
---

### Post by RelativelyQuantum on 2007-06-23
Hi all.

Just a quick question: what xorg.conf settings must I change to enable [Mac style] two finger scrolling? This is something I have seen people do before, and wondered how I might go about setting it up.

Cheers!

-Quantum

---

### Post by tvst on 2007-06-23
```

Section "InputDevice"
     ...
     Driver    "synaptics"
     ...
     VertTwoFingerScroll "true"   # add this line
EndSection

```

more options here:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf)

---

