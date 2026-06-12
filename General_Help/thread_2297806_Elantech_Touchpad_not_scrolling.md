---
title: "Elantech Touchpad not scrolling"
date: 2015-10-06
forum: General Help
---

### Post by jacobmitash on 2015-10-06
I'm fairly new to Ubuntu and recently installed it on my Toshiba Satellite S50C laptop.

Unfortunately, I've discovered that the touchpad is missing features that it had on Windows, the main one being two finger scrolling.

After searching, I've seen most people recommend installing a patch as listed here: [http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/](http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/)

However, this doesn't appear to fix the issue for me despite restarting the driver and Ubuntu.

Here's my xinput list:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Elantech Touchpad                      id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=12    [slave  keyboard (3)]
```

Any advice to getting the scroll feature to work is greatly appreciated.

---

