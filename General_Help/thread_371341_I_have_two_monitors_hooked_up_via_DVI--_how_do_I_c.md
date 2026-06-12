---
title: "I have two monitors hooked up via DVI-- how do I choose primary in TwinView??"
date: 2007-02-26
forum: General Help
---

### Post by billdotson on 2007-02-26
I have an LCD monitor on my right hooked up via DVI and a CRT on the left hooked up using a VGA-to-DVI adapter.  How do I get it so the monitor on the right is my primary monitor??

I have looked in the dualscreen thread but everyone there seems to be using a VGA and a DVI not both.  

Please help as I have gotten the background image fixed already be taking the original image cutting it's width in half and duplicating it and then placing them side by side.

Thank you.

---

### Post by bodhi.zazen on 2007-02-26
What do you mean primary exactly ???

---

### Post by ~LoKe on 2007-02-26
You should attach your /etc/X11/xorg.conf.

---

### Post by Helmi on 2007-03-14
i'll attach here as my problem seems to be similar

i got an geforce 6200 running with the nvidia binary drivers. I setup twinview according to some howto around. I got two 19" TFT attached - one with dvi (my primary one) and one with a crt-cable as the monitors support both. i know would like to setup the dvi as the primary monitor and the other one "rightOf" with the twinview.

The problem is that the CRT always get's known as primary by the nvidia card. 

from my xorg.conf
```

Section "Device"
    Identifier     "NVIDIA GeForce 6200"
    Driver         "nvidia"
    Option	   "TwinView" "True"
    Option	   "TwinViewOrientation" "RightOf"
    Option	   "UseEdidFreqs" "True"
    Option 	   "MetaModes" "1280x1024,1280x1024"
    Option	   "ConnectedMonitor" "DFP, CRT"
    Option	   "UseDisplayDevice" "DFP, CRT"
EndSection

```

the nvidia documents say that the connectedMonitor or UseDisplayDevide option control the primary and secondary stuff, but this doesn't change anything. any ideas?

---

### Post by Helmi on 2007-03-14
ok i found the solution myself

```

Section "Device"
    Identifier     "NVIDIA GeForce 6200"
    Driver         "nvidia"
    Option	   "TwinView" "True"
    Option	   "TwinViewOrientation" "LeftOf"
    Option	   "UseEdidFreqs" "True"
    Option 	   "MetaModes" "1280x1024,1280x1024"
**    Option 	   "TwinViewXineramaInfoOrder" "DFP-0"**
    Option	   "ConnectedMonitor" "DFP, CRT"
    Option	   "UseDisplayDevice" "DFP, CRT"
EndSection

```

---

