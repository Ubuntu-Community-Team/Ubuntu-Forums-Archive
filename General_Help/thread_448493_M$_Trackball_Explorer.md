---
title: "M$ Trackball Explorer"
date: 2007-05-19
forum: General Help
---

### Post by Papillonrus on 2007-05-19
My Ubuntu flavor is 7.04.  Here is the fix for me to enable the Back and Forward buttons on a M$ Trackball Explorer 7 button mouse.  It worked for me and the poster in Linux forums on an M$ LaserMouse 6000.

running Ubuntu Dapper 6.02 beta and I have an M$ LaserMouse 6000 and replacing the /etc/X11/xorg.conf with the code below enabled my side buttons for forward in back in firefox. As noted below, the side buttons do not work in nautilus but I didn't want to mess around with xmodmap since it gave me errors about having 11 buttons

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

---

### Post by funkwurm on 2008-03-21
Just adding my own experience. I have the same MS Trackball Explorer and came across this topic trying to get the button 4 and 5 to work as back/forward in Firefox and hopefully other browsers.

Adding the Buttons and ButtonMapping options wasn't enough for me. I noticed that this configuration has Protocol ExplorerPS/2 and mine had ImPS/2. So I changed it, Ctrl+Alt+Backspace to restart X and it worked, which means:

- Button 4 is back, button 5 is forward, button 3 (scrollwheel) opens link in new tab, some other sources reported that this would break, didn't break for me.

- Works in Netscape 9 as well, but that pretty much Firefox with a Netscape skin, so that figures.

- Doesn't work in Konqueror, but that's their choice of features I guess.

---

