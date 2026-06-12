---
title: "Duplicate icons in Indicator Applet"
date: 2013-11-23
forum: General Help
---

### Post by zeroseven0183 on 2013-11-23
I wonder there are two Wi-Fi network icons displayed on my taskbar. I tried resetting the indicator applet and reloading lxpanel but nothing has changed.

---

### Post by echotech2 on 2013-11-24
I have the same problem(?) only I have two of the up/down arrows.

---

### Post by bobblex on 2013-11-24
I also have the same thing.  
I can get only one to show up, but then my other applets (my-weather and variety) aren't shown.
I've been looking for someway to edit the indicator-applet settings, but have had no luck so far.

---

### Post by walterorlin on 2013-11-24
Do you also have another applet that is provideding the wifi other than indicator applets? If you had manage networks applet and indicator applets and you want to keep the indicator applets then go to your panel right click panel settings click remove on the manage network applet.

---

### Post by bobblex on 2013-11-24
The choice to remove the manage network applet is not presented.  The only choice is 'Remove "Indicator Applets" From Panel'

Removing the "Indicator Applets" also removes other applets in that portion of the panel.  There doesn't appear to be any way to edit what is included in the indicator applet sub-panel.

---

### Post by darkrai425 on 2013-11-26
I've got the same thing going, with two wireless icons.  Trying to find a configuration file...

---

### Post by darkrai425 on 2013-11-26
I resolved the issue:  

edit ~/.config/lxsession/Lubuntu/desktop.conf and remove the line 'network_gui/command=nm-applet'

Upon reboot I now have only a single network icon in the indicator applet

---

### Post by bobblex on 2013-11-26
Thanks, darkai425.  That does in fact fix it for me, too.

---

### Post by zeroseven0183 on 2013-11-29
This one solved it. Thanks darkrai425!

---

