---
title: "Fix Overscan - Custom Arandr Resolution and Permanent at login"
date: 2017-04-06
forum: General Help
---

### Post by markackerman8@gmail.com on 2017-04-06
The title says it all

What Worked!!!!
		
xrandr --newmode "1800x1012_60.00" 151.42 1800 1912 2104 2408 1012 1013 1016 1048 -HSync +Vsync
xrandr --addmode HDMI-1-1 "1800x1012_60.00"
xrandr --output HDMI-1-1 --mode "1800x1012_60.00"

HDMI-1-1 may be different for your screen of course

To Make it run at StartUp

Step 1: Take those 3 commands, save in a set-screen.sh somewhere in your home directory. For example, mine would be in /home/ack/.ScreenLayout/set-screen.sh and that's how it would look like:

#!/bin/sh
sleep 15
xrandr --newmode "1800x1012_60.00" 151.42 1800 1912 2104 2408 1012 1013 1016 1048 -HSync +Vsync
xrandr --addmode HDMI-1-1 "1800x1012_60.00"
xrandr --output HDMI-1-1 --mode "1800x1012_60.00"

Step 2: do in terminal chmod 755 set-screen.sh.

Step 3: Open the Startup Applications and add full path to your file as one of the startup commands.



fewwww Working:o

---

