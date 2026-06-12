---
title: "Xrandr refuse set resolution"
date: 2016-08-21
forum: General Help
---

### Post by jonas-thornvall on 2016-08-21
I have a weird problem with xrandr in openbox, i list all possible resolutions with xrandr i get all possible settings?
And all seem to work except  1360x768 and that is the one i need... a bit strange because there is no problem using graphical interface like arandr.
I would like to do a script that always load the resolution in .config/openbox/autostart the script working but the resolution do not.

jonas@jonas-STCK1A8LFC:~$ xrandr -s 1360x768 
Size 1360x768 not found in available modes

jonas@jonas-STCK1A8LFC:~$ xrandr
Screen 0: minimum 8 x 8, current 1280 x 720, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 1280mm x 720mm
   1920x1080     60.00 +  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1280x1024     60.02  
   1360x768      59.80  
   1280x720      60.00*   50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

---

### Post by banceu_sergiu_ione on 2016-08-21
Does this work ?

```
 xrandr --output HDMI1 --mode 1360x768 
```

---

### Post by jonas-thornvall on 2016-08-21
Work perfectly, thank you! 
But i fail to see the logic when the other modes had no problem using just xrandr -s "resolution", maybe the update frequency weird.

---

