---
title: "Ubuntu 14 lts touchpad settings for HP Envy 15"
date: 2015-03-29
forum: General Help
---

### Post by killid on 2015-03-29
Hi

Hope someone can point me in the right direction?

When I initially installed Ubuntu 14 lts on my new HP Envy 15 all went well and was able to use single finger single tap to select and a single finger double tap to open applications on the launcher.  After transfering some files (pctures and documents) and after installing GIMP Editor my touchpad wouldn't open applications with a single finger double tap.  Double finger taps do work when I manage to keep the pointer over the app. icon

I have looked for advice via the internet and have seen a lot of advice for those wanting to use multi finger taps, scrolls etc but nothing on restoring the very basic single finger setup.  Can someone please help me reinstate single finger taps again.

Many thanks
David

---

### Post by killid on 2015-04-04
Hi
Does anyone have any ideas on how to sort my mess out?  New computer lying idle on my desk, using old one as it works.

Thanks
Desparate David

---

### Post by killid on 2015-04-09
Hi
Can anyone please point me to a web site that may be able to advise me on sorting the touchpad on my HP Envy 15?

Thanks
Very Desperate David

---

### Post by killid on 2015-04-19
Hi
Does anyone have a suggestion to move my query on ?

David

---

### Post by Frogs Hair on 2015-04-19
The following terminal command will display information about various devices . Copy and paste the output it here.
```
xinput --list 
```


Example:```
xinput --list 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                    id=9    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HP HD Webcam [Fixed]                        id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]

```

---

