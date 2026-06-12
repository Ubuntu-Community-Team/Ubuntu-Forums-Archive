---
title: "Another touchpad thread...questions"
date: 2017-09-27
forum: General Help
---

### Post by aeronutt on 2017-09-27
Dell Precision 5510, running Ubuntu Gnome 17.04.
"xinput --list" shows touchpad is recognized as a "SynPS/2 Synaptics TouchPad".

Problem 1:
I installed xserver-xorg-input-synaptics, and tried using synclient. I could change parameters as shown by synclient, but the touchpad itself didn't change. Also, after installing synclient, the GUI changed and had only a few options. So, I uninstalled xserver-xorg-input-synaptics, but the GUI didn't change back to show the original number of options. EG, the option to turn on/off 2-finger scroll is missing. 
So questions:
- How do I get the original GUI options back?
- Any idea why synclient didn't have any effect on the touchpad?

So, going back to trying to use xinput to set parameters:
Problem 2:
Searched and searched, but I can't find the definitions of the parameters as shown by "xinput --list-props", for example "Synaptics Finger (293):	25, 30, 0"

<rant> Every time I load Ubuntu onto a new laptop, I'm disappointed in how it presents the touchpad and touchpad settings. Arguably one of the most important human-machine interfaces. </rant>

Thanks.

---

### Post by aeronutt on 2017-09-30
UPDATE: seems the touchpad I'm actually using is "DLL06E5:01 06CB:7A13 Touchpad" as listed by xinput, rather than Synaptic PS, so I blacklisted Synaptic PS.

But problems remain.

So, new question:

Using synclient, setting TouchpadOff=1 does what it's supposed to (turns off the touchpad).
But none of the other parameters seem to do anything. EG, setting finger pressure (synclient FingerHigh=<num>) does nothing, and my touchpad is FAR too sensitive.

Help!

-

---

