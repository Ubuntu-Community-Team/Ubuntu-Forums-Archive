---
title: "slow touchpad response"
date: 2008-01-08
forum: General Help
---

### Post by aktoads on 2008-01-08
Thanks in advance for any assistance.

I am using Ubuntu on a Toshiba Satellite A15-S157 laptop.  Everything has been seeming well and have been enjoying the experience, until just recently.  (I know, "what did you do recently that changed?" Answer: ??? Nothing out of the ordinary, I think.)  My problem is when I use my touchpad it takes 8 sweeps to move the cursor across the screen, but when I use my USB mouse I have "normal" cursor motion.  I have tried messing with the settings under: System:Preferences:Mouse, this affects the motion only on the USB mouse not the touchpad.  Any ideas, this is getting very annoying.

Thanks again

---

### Post by fragos on 2008-01-08
The following changes to /etc/X11/xorg.conf touchpad section fixed it for me on my Dell 1420n.

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "MinSpeed" "0.5"
        Option      "MaxSpeed" "0.7"
        Option      "AccelFactor" "0.0350"
EndSection

---

