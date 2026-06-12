---
title: "[SOLVED] Touchpad Scroll problem!!! Not a Re-post"
date: 2008-07-05
forum: General Help
---

### Post by justgrant2009 on 2008-07-05
My problem is as follows.  I used to be able to scroll pages with the rightmost part of my touchpad and for some reason it's stopped working, i thought i could just turn it back on but when i go to System>Preferences>Mouse there is no tab for scrolling. I used to be able to scroll but had to change a few things to get my graphics card working one of them asked me if i wanted to emulate a 3 button mouse. First i chose no, then after rebooting, i could no longer scroll, so i ran through the whole reconfig again this time chosing yes to emulate a 3 button mouse, still no luck. Any advice?

I've seen a few other posts about how to fix it but, none of them have solved my issue.

---

### Post by funkydan2 on 2008-07-05
Here's the section of my xorg.conf that is relevant to your setup.  I think it's the last line that you need to ensure is set correctly if you want to be able edit mouse settings using the System>Preferences>Mouse.  You may also want to install gsynaptics which will add a 'Touchpad' entry to your System menu, giving you more control over your touchpad.

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "1"
        Option          "SHMConfig"     "on"
EndSection

---

### Post by justgrant2009 on 2008-07-05
Ok, my input device looks nothing like that:

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

what now?

I tried just copy pasting yours under it, but that changed nothing...

---

### Post by justgrant2009 on 2008-07-05
Wow, never mind, I'm retarded, i forgot to add it to the Server layout after adding it.  Cool man, thanks that helped a lot!

---

