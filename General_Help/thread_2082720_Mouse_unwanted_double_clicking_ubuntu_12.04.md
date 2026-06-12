---
title: "Mouse unwanted double clicking ubuntu 12.04"
date: 2012-11-10
forum: General Help
---

### Post by rjshen43 on 2012-11-10
I have Ubuntu 12.04 on an Acer Aspire 3680 machine.  Sometimes when I  click with my mouse, any one of them(3), not all connected at the same  time, I get a double click response when only clicking once.  They  (mouse) work fine when connected to a windows box.When I use calculator I'll click on a  number and 2 or 3 of that number I click on shows up and I have to  delete unwanted numbers.  When I launch any program like firefox, 2 or 3  Firefoxes open on the bottom panel.  I don't seem to have this problem  with the laptop click button (yet). This problem happens on any mouse I  connect to the Ubuntu 12.04 system and has started recently (maybe with  in the last month or so).
  Has any one else had  this annoying problem, and what to do about it?  

Thank You for your time and expert advice

---

### Post by GreatDanton on 2012-11-10
Try changing Double-click timeout slider in System Settings/Mouse and Touchpad/ Double-Click Timeout.

Hope this helps.

---

### Post by tigerlily09 on 2013-03-24
Bump.

I'm having the same problem. I changed the Double-Click  Timeout slider to its longest setting, but I'm still having issues. If I  hold the mouse button down too long, the OS seems to keep registering  clicks.

This only became a problem since I upgraded from Lucid to Precise.

I double-checked my mouse settings in xorg.conf but they seem to be set to default:

```
Section "InputDevice"

    # generated from default    
    Identifier    "Mouse0"
    Driver    "mouse"
    Option      "Protocol" "auto"
    Option      "Device" "/dev/psaux"
    Option      "Emulate3Buttons" "no"
    Option      "ZAxisMapping" "4" "5"
EndSection
```

I'm only having issues with my (admittedly ancient) Logitech wireless mouse. I tested with my old wired mouse and the Logitech M305 that I use with my laptop and they work fine, but I'd really like to be able to use my plain old wireless mouse.

Thanks in advance.

---

### Post by Shansie on 2013-05-19
Having this same issue in 12.10 with a Logitech USB mouse. I can't use the touchpad on my Dell Inspiron 1545 because it's been wonky for quite some time. I found an old thread on this. Seems like it's been an issue for quite some time.

[http://ubuntuforums.org/showthread.php?t=1371815&page=4](http://ubuntuforums.org/showthread.php?t=1371815&page=4)

---

### Post by rabaggett on 2013-05-19
Yes, Ive had this problem a lot. I solve it by buying a cheap mouse. There seems to be something wrong with the double clicking mice, and I have more than once created a double clicking mouse by dropping it on a hard floor. I have no idea why these 'broken' mice work without fail on M$ (Even in virtualbox!)  This is not confined to Ubuntu. My collection of double clicking mice misbehave on all Linux variants.

On the wireless mouse, I've had these misbehave when the receiver is too close to the wifi antenna, or other sources of noise (Cell or cordless phone?). Try moving the receiver around. The radios in mice and keyboards are often not top quality.

---

