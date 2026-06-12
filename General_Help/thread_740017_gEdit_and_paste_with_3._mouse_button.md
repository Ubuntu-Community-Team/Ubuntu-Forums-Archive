---
title: "gEdit and paste with 3. mouse button?"
date: 2008-03-30
forum: General Help
---

### Post by bigblop on 2008-03-30
For some reason I cannot paste text with the 3. mousebutton in gEdit and geany.  Is this a bug? It works fine in Firefox.

---

### Post by nick_h on 2008-03-30
The middle mouse button works to paste text for me in both gedit and geany.

I'm not quite sure what to suggest as it works in Firefox.

---

### Post by bigblop on 2008-03-30
hm from your signature I can see that you use ubuntu 7.04, maybe it worked in an older version. Whats your version of gedit?

---

### Post by drs305 on 2008-03-30
I'm with nick_h. I can use the middle button with no problems in Gutsy, 32 and 64 bit.

---

### Post by bigblop on 2008-03-31
hm could some of you post your /etc/X11/xorg.conf?

---

### Post by nick_h on 2008-03-31
It also works for me in Gutsy.

Here is the mouse section from my Gutsy xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

---

### Post by bigblop on 2008-03-31
Strange I have the exact same setup, this is my /etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Guess the bug must be somewhere else. But thanks for taking you time to post your config!

---

