---
title: "Getting multi touch on a Lenovo Thinkpad using Touchegg even possible?"
date: 2013-10-04
forum: General Help
---

### Post by jan-goebel-g on 2013-10-04
my xinput:

jan@jan-ThinkPad-L420:~$ xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)] <----thats the touchpad
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=13    [slave  pointer  (2)] 
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]
What i did thus far:
-Disable the synclient stuff.
-On Ubuntu i recompiled a hacked unity to not use the input. 
-Used other distros

Is there anybody with a laptop with "red dot" too? I have to think that its a thinkpad related issue:(
Touchegg doesnt register any gesture at all.

Thanks in advance!!!

---

