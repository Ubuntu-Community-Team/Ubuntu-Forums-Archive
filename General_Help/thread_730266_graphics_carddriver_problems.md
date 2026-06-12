---
title: "graphics card/driver problems"
date: 2008-03-20
forum: General Help
---

### Post by Solid_dean on 2008-03-20
Hi, whenever i install the Nvidia graphics drivers onto my system if i turn the system off and back on or restart i get lines on the initial system screen and then everything goes black and the Scroll lock and caps lock lights flash on my keyboard. I am using a geforce MX440 (bit old now i know) which worked for the last week with the drivers until i left it on for a few hours and came back to the black screen and flashing lights.

I have done a full reinstall of Ubuntu 7.10 with all the updates minus the graphics driver and it works but i cannot get the screen res past 1024x768. 

any help appreciated. thanks

---

### Post by markharding557 on 2008-03-20
add the resolution you want to etc/X11/xorg.conf on the line screen,modes put it first in the list and it should be in that resolution when you restartx or reboot

---

