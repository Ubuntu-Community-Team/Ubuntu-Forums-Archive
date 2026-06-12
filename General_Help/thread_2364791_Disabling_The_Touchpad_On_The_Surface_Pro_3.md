---
title: "Disabling The Touchpad On The Surface Pro 3"
date: 2017-06-28
forum: General Help
---

### Post by SBTlauien on 2017-06-28
When I run 'xinput list' I receieve the following output...

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Surface Type Cover                id=10    [slave  pointer  (2)]
&#9116;   &#8627; NTRG0001:01 1B96:1B05 Pen                   id=13    [slave  pointer  (2)]
&#9116;   &#8627; NTRG0001:01 1B96:1B05                       id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Surface Pro 3/4 Buttons                     id=7    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=8    [slave  keyboard (3)]
    &#8627; Microsoft LifeCam Front                     id=11    [slave  keyboard (3)]
    &#8627; Microsoft LifeCam Rear                      id=12    [slave  keyboard (3)]

``` 

I've disabled each one of these one by one but it appears as if I can only disable my entire keyboard and touchpad together.

I got the touchpad working by adding the below lines to "/usr/share/X11/xorg.conf.d/10-evdev.conf"

```

Section "InputClass"  
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07dc"
        Option "IgnoreAbsoluteAxes" "True"
EndSection 
```

This required a reboot though.  I'd like to be able to enable/disable my touchpad without rebooting.  I can do this on my laptop and made a small python indication that allows me to switch it on/off.  I'd like this to work on my SP3 as well.

Thanks in advance.

---

### Post by SBTlauien on 2017-06-29
Bump

---

### Post by SBTlauien on 2017-07-02
Bumper.

---

