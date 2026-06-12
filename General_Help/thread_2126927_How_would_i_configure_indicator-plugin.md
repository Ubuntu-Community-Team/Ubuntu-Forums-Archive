---
title: "How would i configure indicator-plugin?"
date: 2013-03-18
forum: General Help
---

### Post by Psil0cybin on 2013-03-18
I have the system monitor graph, on the left side i have the volume and mail plugins, and on the right the wifi and battery. I would like to move all icons to one side, I have played around with[B] panel > panel preferences > icons
[/B]I also tried moving the whole indicator icon to the right before the time plugin, that also didnt work just made a different mess.
I have tried moving them around, but the indicator plugin moves the icon and volume with it. 
(When I remove the indicator-plugin, I lose my Volume and Mail button all together)
I want to keep the graph on the left, and all the icons on the right. 

[IMG]http://oi46.tinypic.com/2nm8hf.jpg[/IMG]
Here is my current example.
I just want to move the volume and mail icon to be beside the Wifi and Battery...
Thanks in advance

---

### Post by LewisTM on 2013-03-18
In Panel -> Panel preferences -> Items, put the items in the right order, from left to right, starting with the System monitor. Insert a separator after the monitor and set it to Expand. It will take up all the available room in the center and the rest (indicator, notification area, etc) will be aligned to the far right.

Cheers!

---

### Post by Psil0cybin on 2013-03-18
There is no system monitor it seems to be integrated into the indicator panel (the panel holds the buttons along with the graph) for some reason...would this still work?

It shows a default list of the following
Application Menu
Windows Buttons
Seperator
Indication Plugin
Notification Area
Date Time
Seperator
Windows Switcher
Session Manager

---

### Post by r.stiltskin on 2013-03-18
Umm ... are you using gnome-panel (as opposed to xfce4-panel)?  In xfce4-panel my mail icon is in the Notification Area, not part of the Indicator Plugin.

If you're using gnome-panel you might want to change your thread prefix, or at least make that clear in your post.

---

### Post by Merrattic on 2013-03-18
You need to be here if using xfce4-panel, and adjust items accordingly

[ATTACH=CONFIG]240331[/ATTACH]

---

