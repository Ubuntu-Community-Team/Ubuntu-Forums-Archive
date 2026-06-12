---
title: "firefox mouse back/forward"
date: 2007-02-26
forum: General Help
---

### Post by h0lix on 2007-02-26
I just recently upgraded to dapper from Breezy. When i did the upgrade i did it with a fresh install. Before, I followed the howto in the [http://www.ubuntuforums.org/showthread.php?t=44191](http://www.ubuntuforums.org/showthread.php?t=44191) thread and got my back and forward side buttons on my m$ intellimouse 3.0a to work just fine. After upgrading i tried to make the same modifications to my xorg.conf with no such luck. 

I also tried to use the howto thread [http://gentoo-wiki.com/HOWTO_Advanced_Mouse](http://gentoo-wiki.com/HOWTO_Advanced_Mouse) which is a gentoo thread but i remember reading somewhere that it should work in ubuntu. 

Now, somehow or another my side buttons do work as if they were a normal left-click on the mouse and at one point i had the back/forward working but it was bound to my mousewheel.

Below is the mouse section of my xorg.xonf file:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

any insight would be greatly appreaciated. I just cant figure out why i could get it to work in breezy and not in dapper.

---

### Post by bergersau on 2007-02-26
The  wheel(z axis) is 4 and 5.
6 and 7 are your forward and back buttons.

Try this:

First, back up your xorg.conf file.
Code:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Edit your xorg.conf by typing the following into the terminal:
Code:

sudo nano /etc/X11/xorg.conf

Note: I use nano as my text editor, you may be using others such as gedit.

Find the InputDevice section that has to do with your mouse. It should look similar to this:

Code:

Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
... 
EndSection

Edit it so it looks like this:

Code:

Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
Option "CorePointer" 
Option "Device" "/dev/input/mice" 
Option "Protocol" "ExplorerPS/2" 
Option "ButtonMapping" "1 2 3 6 7" 
Option "ZAxisMapping" "4 5" 
EndSection

Save the amended xorg.conf file.

Restart your computer, start up your browser, and it should work!



Credit:
Essentially a re-post of the solution given by  Blazeix in another thread.

---

### Post by h0lix on 2007-02-27
Works great! Thank you so much!

---

