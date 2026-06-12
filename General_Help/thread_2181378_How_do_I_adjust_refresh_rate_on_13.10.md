---
title: "How do I adjust refresh rate on 13.10?"
date: 2013-10-17
forum: General Help
---

### Post by Shenza on 2013-10-17
Alright, so I just installed Ubuntu 13.10, its pretty interesting so far, but after applying the nvidia-319 proprietary driver, the refresh rate seems a bit off, like it could be better. I remember on 13.04 there was an issue with compiz config composite settings where the refresh rate would automaticaly reset to 50 after each restart. I dont think 13.10 uses compiz, but anyhow how can I adjust the refresh rate to at least 60, im not seeing it anywhere in settings???

---

### Post by Shenza on 2013-10-17
Alright, I played around with some stuff in hopes to find an answer. So far this is what I have done...
Open Nvidia X Server Settings, click where it says X Server Display Configuration, go to Resolution, change it from Auto to whatever you prefer, then it allows you so select either 50hz or 60hz right next to it. Seems like it will solve the issue, but sadly it resets after restart even after you hit the apply button. So, im out of ideas.

---

### Post by mc4man on 2013-10-17
> **Shenza said:**
> Alright, I played around with some stuff in hopes to find an answer. So far this is what I have done...
Open Nvidia X Server Settings, click where it says X Server Display Configuration, go to Resolution, change it from Auto to whatever you prefer, then it allows you so select either 50hz or 60hz right next to it. Seems like it will solve the issue, but sadly it resets after restart even after you hit the apply button. So, im out of ideas.

If on an ubuntu session (unity) then compiz is being used, though shouldn't be a factor here.
As far as nvidia-settings - did you click on the button to write your changes to  xorg.conf?
This should show you your current refresh rate - in terminal
xrandr

---

### Post by Shenza on 2013-10-18
> **mc4man said:**
> If on an ubuntu session (unity) then compiz is being used, though shouldn't be a factor here.
As far as nvidia-settings - did you click on the button to write your changes to  xorg.conf?
This should show you your current refresh rate - in terminal
xrandr

Yeah I saved a xorg.conf file, under monitor I get this. But this is now on xubuntu, im gunna hold off on ubuntu for a while. 13.10 is a so new they may need to work a few things out....but on xubuntu things seem ok....

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+   59.9     50.0     60.1     60.0     50.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       59.9  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0     59.9     50.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9     59.9

---

