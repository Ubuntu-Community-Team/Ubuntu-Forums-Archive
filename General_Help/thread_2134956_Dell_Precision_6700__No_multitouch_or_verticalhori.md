---
title: "Dell Precision 6700  No multitouch or vertical/horizontal scroll"
date: 2013-04-12
forum: General Help
---

### Post by Grafens on 2013-04-12
Hello
I posted this a week ago on the dell support thread but got no response, so I'm posting it again here.
I have a dell precision. My touchpad works but without multitouch vertical/horizontal scroll functions, synaptiks is installed but cannot find it and so I get an error every time I boot up.
here's the output for xinput -list

```
xinput -list&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet stylus     id=10   [slave  pointer  (2)]
&#9116;   &#8627; Logitech HID-compliant mouse              id=12   [slave  pointer  (2)]
&#9116;   &#8627; Logitech HID-compliant mouse              id=13   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                        id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_E4HD             id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=16   [slave  keyboard (3)]
```
Help would be much appreciated
Thanks

---

### Post by mac-duff on 2013-10-03
Hi,
I dont know if this helps but I had also a problem with with touchpad and scrolling.
I had to chenge in dconf this one:
org.gnome.settings-daemon.peripherals.touchpad -> scroll-method: "edge-scrolling"

---

