---
title: "getiing touch pad to work"
date: 2008-03-03
forum: General Help
---

### Post by zigNzag on 2008-03-03
i got a new dell inspiron 1420 and i cant get the touch pad to work decent. i downloaded touchpad but i gives me a error when i try to use it:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

plz help

---

### Post by zigNzag on 2008-03-03
bump

---

### Post by Rocket2DMn on 2008-03-04
Open a terminal and run
```
gksudo gedit /etc/X11/xorg.conf
```
Find the line for "SHMConfig" and set the next set of quotations to "true".
If you can't find that line, add it between the lines 
```
Section "InputDevice"
       Identifier "Synaptics Touchpad"
       ............
EndSection
```

If you post xorg.conf, I can help you with it.

---

### Post by zigNzag on 2008-03-04
touch pad loads now but when i use the options to make my touch pad faster or more sensitive nonthing happens it just stay the same speed.

---

### Post by Rocket2DMn on 2008-03-04
Hrmm, not really sure what's going on there.  Are you using System->Preferences->Mouse
Post your xorg.conf file for me:
```
cat /etc/X11/xorg.conf
```
Also, did you restart X?  To do that, save all your open files and whatnot and do CTRL+ALT+BACKSPACE

---

### Post by Jamezracer on 2008-03-06
I'm having the same problem with the dell touchpad. Worked in gutsy, but now with 8.04 alpha I get the same error message. I can use the mouse, but can't open the touchpad settings manager to get scrolling to work. I've modified the xorg.conf file trying both "true" and "on" as I've seen it both ways. no luck, as soon as I find the XF86Config file I'll let you know if that fixes it

---

### Post by Rocket2DMn on 2008-03-06
Jamezracer, remember that Hardy is still in the alpha stage, and they are also using a newer version of Xorg.  Try auto-regenerating xorg.conf with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE

---

