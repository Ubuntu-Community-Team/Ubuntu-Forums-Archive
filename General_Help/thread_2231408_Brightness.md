---
title: "Brightness"
date: 2014-06-25
forum: General Help
---

### Post by lunaservant on 2014-06-25
I recently hooked up a second monitor to my laptop but the monitor has a brightness issue.  I turned up the monitors brightness to max and even used the AMD catalyst Control Center to up the brightness further, but if I take it any further than it already is then the laptops main screen will be too bright.  Is there a way to increase the brightness of the second monitor without increasing the brightness of the main monitor?

I am using Ubuntu 14 if that helps.  if you need further info just ask.

---

### Post by lunaservant on 2014-06-25
I recently hooked up a second monitor to my laptop but the monitor has a brightness issue.  I turned up the monitors brightness to max and even used the AMD catalyst Control Center to up the brightness further, but if I take it any further than it already is then the laptops main screen will be too bright.  Is there a way to increase the brightness of the second monitor without increasing the brightness of the main monitor?

I am using Ubuntu 14 if that helps.  if you need further info just ask.

---

### Post by oldfred on 2014-06-25
merged duplicate threads.

Please only post one thread per issue.

---

### Post by lunaservant on 2014-06-25
sorry about that.  When I posted the first one I received an error so I didn't think it posted.  I should have checked.

---

### Post by Toz on 2014-06-25
You can try using the brightness parameter of xrandr to set brightness values. Here is how to do it.

First, identify the names of your displays using the command:
```
xrandr -q | grep " connected" | cut -d' ' -f1
```
For me, my LCD is "LVDS1" and my external monitor is DP2.

Then, use xrandr to manually adjust the brightness of that display (note the brightness value needs to be between 0 and 1.0 in decimal increments). As an example, to decrease my external monitor brightness in half, I would use the command:
```
xrandr --output DP2 --brightness 0.5
```

You may need to fine tune the brightness setting for both displays to get them the way you want them (lower the LCD and raise the external).

---

### Post by lunaservant on 2014-06-25
> **Toz said:**
> You can try using the brightness parameter of xrandr to set brightness values. Here is how to do it.

First, identify the names of your displays using the command:
```
xrandr -q | grep " connected" | cut -d' ' -f1
```
For me, my LCD is "LVDS1" and my external monitor is DP2.

Then, use xrandr to manually adjust the brightness of that display (note the brightness value needs to be between 0 and 1.0 in decimal increments). As an example, to decrease my external monitor brightness in half, I would use the command:
```
xrandr --output DP2 --brightness 0.5
```

You may need to fine tune the brightness setting for both displays to get them the way you want them (lower the LCD and raise the external).

this particular solution did not work but it did lead me to a solution that did work.  I discovered that I had AMD Catalyst setup for one desktop on two screens (basically it was one extra wide desktop) which is why the brightness settings didn't have any effect.  I changed it to a multi-display desktop and it allowed me to change the brightness setting of the second monitor withing the catalyst controls.

---

