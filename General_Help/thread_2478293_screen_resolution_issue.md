---
title: "screen resolution issue"
date: 2022-08-22
forum: General Help
---

### Post by cmcanulty on 2022-08-22
I recently changed to a new monitor 24" with 1920x1080. This gives a nice clear screen. However every app I open opens off screen or partially off screen. How can I make the resolution apply to every app? See screenshots[ATTACH=CONFIG]290896[/ATTACH][ATTACH=CONFIG]290897[/ATTACH]

---

### Post by Yellow Pasque on 2022-08-23
I see you're using xfce. The first thing I'd try is this:
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
```
Basically, it will erase xfwm's "memory" of your old resolution and displays. A fresh file will be automatically generated the next time you log in.

---

### Post by cmcanulty on 2022-08-24
Thanks, but unfortunately that didn't fix anything. Any other tweaks or do I have to abandon my new monitor?

---

### Post by col48 on 2022-08-24
I had something similar a long time back - the screen origin and the monitor display origin were not the same.

This was eventually resolved by changing the screen geometry **on the monitor**.  Nothing to do with the OS.

Worth a look.

---

### Post by Yellow Pasque on 2022-08-24
^Yes, please tell us the model number of the monitor and look at:
```
xrandr -q
```

---

### Post by cmcanulty on 2022-08-24
[ATTACH=CONFIG]290909[/ATTACH]

```
cmcanulty@Dell660s:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 880mm x 490mm
   1920x1080     60.00*+  50.00    59.94    24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1440x900      59.90  
   1360x768      60.02  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  
DP-1 disconnected (normal left inverted right x axis y axis)
cmcanulty@Dell660s:~$ 
```

Model is a 24" sceptre TV model E24[ATTACH=CONFIG]290909[/ATTACH]

---

### Post by cmcanulty on 2022-08-24
How do I do that? I just noticed now display says 19" monitor it did say 24" which is correct. However the same problem exists either way. The resolution looks good but every single window I open has to be resized to see the whole window.

---

### Post by Yellow Pasque on 2022-08-24
Does your monitor/TV have an aspect ratio setting?

---

### Post by cmcanulty on 2022-08-24
wow I found the remote and it had an aspect ratio setting and that was it, thank you!!!

---

