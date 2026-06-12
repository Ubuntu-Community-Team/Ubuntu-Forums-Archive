---
title: "Trackpad dies when suspending"
date: 2016-06-18
forum: General Help
---

### Post by PikCeLL on 2016-06-18
Hello,

First of all I hope I'm in the right place.
My problem is that when I suspend my computer (with Ubuntu 16.04), my trackpad disappears and I have to reboot to get it back. This is very annoying as suspending happens when I close the lid.

To illustrate the problem I found that I could get some informations about the touchpad with these commands : 
```
$ egrep -i 'synap|alps|etps' /proc/bus/input/devices
$ xinput list "$(egrep -i 'synap|alps|etps' /proc/bus/input/devices |cut -d'"' -f2)"

```

When doing this before suspending I get, respectively :
```
N: Name="ETPS/2 Elantech Touchpad"
```
and
```
ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
    Reporting 10 classes:
        Class originated from: 12. Type: XIButtonClass
        Buttons supported: 12
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None None None
        Button state:
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: 0.000000 - 3097.000000
          Resolution: 31000 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: 0.000000 - 2119.000000
          Resolution: 32000 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Scroll
          Range: 0.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Vert Scroll
          Range: 0.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 4:
          Label: Abs MT Touch Major
          Range: 0.000000 - 2445.000000
          Resolution: 0 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 5:
          Label: Abs MT Pressure
          Range: 0.000000 - 255.000000
          Resolution: 0 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 12. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 75.000000
          flags: 0x0
        Class originated from: 12. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: 75.000000
          flags: 0x0
        Class originated from: 12. Type: XITouchClass
        Touch mode: dependent
        Max number of touches: 5

```

This looks normal, but when I try that after suspension , they give not result at all...
After some researches I found a solution implying a /etc/pm/sleep.d/0000trackpad script but it was on a much older thread (ubuntu 13) and did not help me at all.

Any help would be very appreciated and I'd like to thank those who will look into this in advance :)

---

### Post by QDR06VV9 on 2016-06-18
This has been reported as a bug since 2015 Witch first showed up here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130)
New bug for Xenial
[https://bugs.launchpad.net/ubuntu/+bug/1573454](https://bugs.launchpad.net/ubuntu/+bug/1573454)
There was a patch that was successful  for a handful of users that went something like this
```
sudo gedit /etc/pm/sleep.d/0000trackpad
```
and add the following
```
#!/bin/sh
case "$1" in
    suspend|hibernate)
        modprobe -r psmouse;
    resume|thaw)
        modprobe psmouse;
esac
```
But there was a side effect that the laptop would no longer sleep.
You may have to change _**0000trackpad **_to your device don't know for sure.

---

