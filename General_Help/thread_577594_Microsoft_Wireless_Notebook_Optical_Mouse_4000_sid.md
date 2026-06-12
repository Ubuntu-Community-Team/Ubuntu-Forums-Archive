---
title: "Microsoft Wireless Notebook Optical Mouse 4000 side button"
date: 2007-10-16
forum: General Help
---

### Post by delfick on 2007-10-16
hello

I have recently (today :D) bought a Microsoft Wireless Notebook Optical Mouse 4000 

but i can't for the life of me configure the one side button....

In xev, it registers the side button as button 3 (every other button is correct)

here is the relevant section of my xorg.conf file

> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Buttons"       "6"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option         "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 2 3 4 5 6"
EndSection


can anyone point out how I could possibly solve this issue, so that the side button is registered as button 6 and be used as the back button in the browser ??

thnx :D

---

### Post by daou on 2007-10-16
Try changing the Protocol to "auto" and Device to "/dev/psaux"... if, after that, you have trouble with binding the key to a certain function, you can use btnx for that:
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

However, btnx might be overkill for the mouse: the ButtonMapping option should be enough.

---

### Post by delfick on 2007-10-16
thankyou for that

unfortunately, those settings in xorg.conf make it so that the side button isn't even registered by xev

and when I try btnx, it doesn't work (when I try to detect mouse and it tells me to wait 5 seconds, it doesn't do anything, even after many minutes.....)

....

---

