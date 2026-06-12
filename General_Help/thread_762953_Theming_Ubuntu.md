---
title: "Theming Ubuntu"
date: 2008-04-22
forum: General Help
---

### Post by gavinjb on 2008-04-22
Hi,

I have been trying to Theme Ubuntu to get rid of the brown and replace with a nice Blue, only problem is whatever I try I always seem to get a brown screen before my Wallpaper loads, I have tried setting the colour option in both gdmSetup and Appearance Settings (Under Background), but this has made no effect.

Also I seem to have a problem with the logon not always completing, for example if I make a configuration change and logout to see the change I have to reboot the machine, if not the logon gets about halfway through (I have the menu bar and brown screen) and then it just sops and all I can do is Ctrl + Alt + Backspace and then select reboot

---

### Post by chrisccoulson on 2008-04-22
If you're running Gutsy, then that is a well known bug and it's on Launchpad somewhere. Sorry, I can't remember the number for it though

---

### Post by gavinjb on 2008-04-22
Hopefully Hardy sorts out some of the Gutsy problems, as I have found Gutsy to be very buggy compared to Feisty and Edgy.

---

### Post by Achtung on 2008-04-22
One workaround is editing this file:
/etc/gdm/PreSession/Default

Near the end of the file, you'll see this:
```
# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#dab082"
```
(... Ctrl+F "dab082" to find it quickly). The "dab082" is the brown colour. Change this to another colour not to see the brown anymore. I set mine as "000000" to get a black screen.

---

### Post by gavinjb on 2008-04-22
Thanks that changed the colour

---

