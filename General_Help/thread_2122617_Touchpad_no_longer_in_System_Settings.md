---
title: "Touchpad no longer in System Settings"
date: 2013-03-05
forum: General Help
---

### Post by mhusz on 2013-03-05
I've been running 12.04 64-bit on my laptop for about a month, and this morning all of a sudden the touchpad works only as a mouse. I checked Mouse and Touchpad in System Settings, and the Touchpad tab is missing.

Any ideas?
The hardware seems to be recognized just fine, and looking in the usual places (var/log/syslog, dmesg, xinput) things look normal. I'm at a loss.

This is a Dell inspiron 1420 laptop.

No errors in /var/log/syslog


dmesg | grep ALPS
[   12.059148] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10


xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Broadcom Corp                               id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Broadcom Corp                               id=9    [slave  keyboard (3)]
    &#8627; Laptop Integrated Webcam                    id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]

---

