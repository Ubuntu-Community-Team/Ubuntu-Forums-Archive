---
title: "Logitech MX300 - 6 Button Mouse"
date: 2007-04-11
forum: General Help
---

### Post by Darko Beta on 2007-04-11
I searched the forums and the internet and could not find instructions on getting my Logitech MX300 mouse's "extra" (6th) button to work as a back button in Firefox.  However, I referred  to the widely available instructions for 7 button mice, and tinkered a bit with my xorg.conf and finally hit upon the right combination.  I am posting the mouse section of my xorg.conf to help anyone in the future who might search for this information for an MX300.

> Section "InputDevice"
     Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "6" 
    Option         "ButtonMapping" "1 2 3 6"
EndSection

---

### Post by Ek0nomik on 2007-05-04
Did you simply add this to /etc/X11/xorg.conf?

I have an MX300 and I added that to it and I didn't have any luck.  :/

---

### Post by KaiserMonkey on 2007-05-17
Thank you very much! This fixed one of the only two errors I've had with Ubuntu (the other, my sound not working, is already fixed).

---

### Post by kovan on 2008-01-22
I love you so much!. This issue has been bugging me for so much time!.

---

