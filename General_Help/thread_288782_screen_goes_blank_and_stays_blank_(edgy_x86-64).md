---
title: "screen goes blank and stays blank (edgy x86-64)"
date: 2006-10-30
forum: General Help
---

### Post by isellapples on 2006-10-30
hi, i had the same problem with the 6.06 version, where the loaders  would appear, everything loads fine but the desktop just doesnt appear on the screen - i got around this by using the safe mode for graphics, and once installed everything was fine

but the problem is still there in edgy, except the safe mode doesnt help this time. everything loads fine (i get the sounds when its all logged in), and i can restart the kernel [that what its called?](ctrl, alt backspace thingy, more sound). i can even move the mouse to the top left corner to click on applications and the CD will spin to load the list, but the screen just wont show anything. below are my specs

Laptop (acer ferrari 4005), Turion64 ML-37, 1gb, X700 mobility

any suggestions would be great - could i install 6.06 and then update it using the online updates system?

EDIT: Oh, and the CDs dont have any errors on them

---

### Post by vbhtngr on 2006-11-02
1. After you hear the sounds, wait for a while and press ctrl-alt-F1

2. On the prompt, vi /etc/X11/xorg.conf

3. Look for the section "Device"

4. Put the following lines under that :

Option     "CRT2Position" "clone"
Option     "MonitorLayout" "LVDS,CRT"

5. Save the file

6. On the prompt. init 5

This should get you working, though not with a very good resolution, but you can get it installed. Hope this helps.

---

