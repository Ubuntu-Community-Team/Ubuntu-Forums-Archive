---
title: "Blender crashes constantly!"
date: 2007-03-26
forum: General Help
---

### Post by anemon on 2007-03-26
I worked with Blender for quite a while before I made the switch from Windows to Linux, and it really is a great piece of software. Just too bad I can't seem to get it to work in Ubuntu! Which is kind of wierd because, to begin with, it's in the repos -- so it should be more or less fail-safe, right?  ;-) And it's not just that it doesn't work, but it does so (i. e. not work) in a very ... well, relentless, way. It just crashes. 

Crashes, crashes, crashes. 

Well, here's the story. Every time I start it up, it runs normally for some five or ten seconds, and then it closes down unexpectedly. And, more often than not, my entire system freezes as a consequence! I've tried both v. 2.42a (the one in the repos) and the new 2.43, but the result is always the same: a cold reboot and a sting of frustration...

Anything else? Oh, while the program is actually up and running (those few precious seconds), it seems that the menus are kinda lagging. Is there something wrong with the graphics drivers? I'm on a brand new ASUS + Core 2 Duo machine, so the hardware is hardly the problem.

Please help!

---

### Post by FluffyElmo on 2007-03-26
This is almost certainly a graphics driver issue. The open source graphics drivers generally don't support OpenGL or 3D acceleration which Blender uses heavily. If your system uses ATI or Nvidia graphics install the latest driver for your system and see if that fixes the problem. 

Here is a link with instructions on installing the Nvidia drivers, if you search the forum you'll probably find similar posts for ATI or other vendors...
[http://ubuntuforums.org/showthread.php?t=301499]("http://ubuntuforums.org/showthread.php?t=301499")

If that doesn't help try running blender from a terminal window and post the output along with your hardware information. Run *Applications->Accessories->Terminal* and type *blender* then hit *Enter* or *blender -d* to turn debugging on.

---

### Post by anemon on 2007-03-26
Oh yeah, the ATI drivers. I used to have them installed, but switched back to open source for some reason -- did it have something to do with Beryl? Don't remember. Anyhow, I installed them anew using Envy, and now Blender seems to work just fine! Haven't tried to do much, but the menus aren't lagging, which is always a good sign...

On the other hand, K-3D *stopped* working. It won't even start, just gives me the error message
```
GdkGLExt-WARNING **: cannot load PangoFont
```
and a seg fault. Guess you only need one 3D app at a time, though. ;-)

Anyway, thanks for the driver tip! Kinda obvious, but I'm a subtle guy. (Whatever that is supposed to mean.)

---

### Post by FluffyElmo on 2007-03-26
No problem, glad I could help. I know from my own problems that the obvious solution is often the last one I think of :) Can't help with K-3D, though that sounds like a driver related error. Maybe try completely removing and reinstalling...probably won't solve it but it can't hurt.

Good Luck!

---

### Post by anemon on 2007-03-27
One more thing, though. Since I swiched drivers, my login screen doesn't display right: whatever settings I choose in System > Administration > Login screen, the monitor goes blank and says the signal does not comply with its recommended resolution (1680x1020, if I remember right). 

Any ideas on this? Where can I change the display resolution for the login screen?

---

### Post by FluffyElmo on 2007-03-27
It goes through the resolutions set in your xorg.conf and usually picks the largest. Nvidia has an administration applet that will configure it, maybe ATI has something similar. You can always edit your xorg.conf file (*/etc/X11/xorg.conf*) to remove all the resolutions other than your panels native one. Just back it up first:) If X won't run, Ctrl-Alt-F2 will get you to a terminal to undo the changes.

---

### Post by anemon on 2007-03-28
Well, the xorg.conf looks all right to me. The thing is that the resolution is perfect as soon as I log in, but the login screen never displays right. So it can't have anything to do with X as a whole... Beats me!

---

### Post by Offoffoff on 2007-11-05
Your problem is not problem, man. I can not even start Blender. I am thinking it is due my Compiz-Fusion, but I do not like to switch off effects.
This is the debug log:
guessing 'blender-bin' == '/usr/bin/blender-bin'
Blender 2.44 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Color depth r 5 g 6 b 5
Aux buffers: 0
read file 
  Version 242 sub 4
read file 
  Version 241 sub 0

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/alien/.blender/Bpymenus

Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Segmentation fault (core dumped)

---

