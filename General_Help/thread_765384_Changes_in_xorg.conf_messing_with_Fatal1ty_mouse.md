---
title: "Changes in xorg.conf messing with Fatal1ty mouse"
date: 2008-04-24
forum: General Help
---

### Post by rotten777 on 2008-04-24
So after upgrading to Hardy (yay!) I have now had to start using my middle button as my right mouse button. Any idea what needs to be changed?

From xorg.conf

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

```

---

