---
title: "Mouse and Live CD, again"
date: 2005-08-21
forum: General Help
---

### Post by whitroth on 2005-08-21
Ok, I'm still looking for help. I cannot get Kubuntu to recognize my old Logitech serial mouse.

From my running system, (RH Shrike) XF86Config:

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "MouseMan"
        Option      "Device" "/dev/ttyS1"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "no"
EndSection

I found and brought up xorgcfg, and used keyboard buttons to set it to Logitech, S1, and no emulate, hit "apply changes", and nothing happens.

So I tried to do init s, and the whole windowing system freezes, and the keyboard's dead.

Can anyone give me some help? I'd really rather not give up on Ubuntu....

             mark

---

