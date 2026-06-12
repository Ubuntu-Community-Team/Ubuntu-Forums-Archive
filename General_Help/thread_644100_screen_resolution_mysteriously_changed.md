---
title: "screen resolution mysteriously changed"
date: 2007-12-18
forum: General Help
---

### Post by pennyminstrel on 2007-12-18
I've got a dual boot setup with Windows XP and Ubuntu. I just restarted and instead of any of the usual startup stuff the screen looks like fabric which changes colours a few times and then displays the message 'Out of range'. Along the top of the message box it says '640x480', so presumably the screen resolution has some how got changed without my knowing it.

The machine sounds as if its starting up ok and sure enough if I plug another screen in its fine. I can't get to change the settings as all it shows is this strange backgroundy-looking thing. I've searched the forums and can't find a similar problem.

Anyone got any suggestions?

---

### Post by geraldm on 2007-12-18
on 'Out of range' :  When X starts it uses parameters for several different sized screens, to see if the parameters allow timings for a specific standard size.  If not, it provides a message for "Out of range' for horizontal or vertical sync.
The resolutions are defined in file /etc/X11/xorg.conf 
There should be another file that has more clues, in the home directory of the user that logged in.  The file is ~/.xsession-errors

The settings can be changed by using a fail-safe type of boot, or by using a rescue CD or liveCD.
Be sure to backup the xorg.conf file before you make any changes to it, if you do decide to edit it.

Gerald

---

