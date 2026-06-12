---
title: "ThinkPad T61 brightness"
date: 2014-03-13
forum: General Help
---

### Post by Redalien0304 on 2014-03-13
Just got a Lenovo ThinkPad T61 Laptop. Liking it so far. The Screen Brightness seems Dimmer from My previious Lappy Dell D830 (which has Video card Failure or Heatsink Issues. Not sure yet.) But my T61 is slow to come up from Screen lock? Is this normal for this laptop?? I have tried using the Fn Brightness to make it Brighter. Any help would be Appreciated thanks.

---

### Post by tgalati4 on 2014-03-13
I have a T43p which is an older version than yours.  The backlight inverters go bad and the screens go dim.  Fortunately the parts are available and you can find videos on how to change it.  Not easy, but not impossible.  The slow wake up from sleep is the inverter slowly coming up to voltage to increase the brightness.  My T43p comes up in about 8 seconds from sleep.  Does your screen have a pinkish color?  Does your screen flicker at all?

A simple google search brings up:

[http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T61-LCD-low-brightness/td-p/1068713](http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T61-LCD-low-brightness/td-p/1068713)

[http://forums.anandtech.com/showthread.php?t=204931](http://forums.anandtech.com/showthread.php?t=204931)

[http://linux-thinkpad.10952.n7.nabble.com/Low-LCD-brightness-on-T61-td9023.html](http://linux-thinkpad.10952.n7.nabble.com/Low-LCD-brightness-on-T61-td9023.html)

These are business machines, have matte screens, low-contrast, and not designed to use at the beach.  So the screens basically suck, but run Linux well otherwise.

---

### Post by kurt18947 on 2014-03-13
Re changing the backlight inverter (or anything else),  Lenovo has continued to make available service & repair manuals online.  Having the manual available has helped answer the question "Why won't this thing come apart?" a time or two.

---

### Post by Redalien0304 on 2014-03-14
No Pinkish screen color & no screen flickering that i have noticed.

---

### Post by ofnuts on 2014-03-14
Used to have a T61 with Lucid and things worked OK. Never noticed any kind of "slowness" when unlocking the screen (but can you be more accurate about what is slow?).

What desktop & screen manager are you using?

---

### Post by Redalien0304 on 2014-03-14
slow is  about 5-6 Secs coimg on from Lock Screen. I am using Cinnamon Desktop  with Unity & Nautilus removed.

---

### Post by ofnuts on 2014-03-14
I still doubt it's a problem with the hardware (or with Lenovo drivers). It is possible to hook scripts to the unlock event, maybe one of these is slow?

---

### Post by Redalien0304 on 2014-03-14
using hook scripts i do not know how to do?

---

### Post by tgalati4 on 2014-03-14
Check your log files in /var/log (pm-suspend.log and pm-powersave.log) and see what is going on.  Use a phone app to measure screen brightness and compare it to published specs for your laptop.  IBM/Lenovo use TFT displays which are not as bright as IPS displays used on other laptops.

---

