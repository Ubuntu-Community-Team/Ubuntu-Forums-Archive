---
title: "No touchpad right click Acer aspire D255 after upgrade to 12.04After"
date: 2013-12-25
forum: General Help
---

### Post by exepcis on 2013-12-25
After upgrading to 12.04 my touchpad works but the right click function disappears  after some time

```

 xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=13    [slave  keyboard (3)]


```
I downloaded the enable-rightbutton.sh but by executing i get
```

./enable-rightbutton.sh 12
property Synaptics Soft Button Areas doesn't exist, you need to specify its type and format

```


Its very anoying andi am clueless what to do

---

