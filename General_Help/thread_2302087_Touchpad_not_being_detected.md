---
title: "Touchpad not being detected"
date: 2015-11-07
forum: General Help
---

### Post by chris_seadon on 2015-11-07
I have an HP pavilion 15-n096sa. I recently installed Ubuntu, and the touchpad won't work in any circumstance. It didn't work in the live session, and it still doesn't work after installing. I have ran xinput -list and discovered that the OS isn't detecting the touchpad at all (I'll put the output here just in case, however). I've also tried doing **modprobe -r psmouse** and **modprobe psmouse proto=imps**. Has anybody got any idea how to get it to show up?

The output of xinput -list:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=12    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=13    [slave  keyboard (3)]


```

---

