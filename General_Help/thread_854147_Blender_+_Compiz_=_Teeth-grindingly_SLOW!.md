---
title: "Blender + Compiz = Teeth-grindingly SLOW!"
date: 2008-07-09
forum: General Help
---

### Post by memories on 2008-07-09
If I have compiz running (which is all the time), Blender is too slow in full screen mode. That's an understatement actually. It's somewhere between 'slow' and 'frozen'.

With compiz off, it becomes usable.. though I still think it can be faster. It's faster on my XP box which has almost half the specs I'm running Linux on. 

Turning compiz off is not a real solution. Maybe it's ADHD, but I like to use Blender while I'm doing other things (FF open, Gaim, Rhythmbox, a few nautilus instances. Though running it alone doesn't fix the problem either. 

The -w option helps a little:
**blender -w -p 0 0 1270 945**

but the difference isn't that significant..


No noticeable problems with any other apps. Stellerium runs fine in fullscreen.

Nvidia GeForce 6600GT, PCI-express 16x
nVidia drivers installed manually from nvidia binary

> 
$ glxinfo | grep dir
direct rendering: Yes


> 
$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!


Running latest version of Nvidia drivers, Hardy, Compiz and Blender
[B]
help! [/B]

---

### Post by sandos on 2008-10-17
I have the same problem. I am guessing blender wants to use memory/resources the driver is unable to give it with compiz active. This thing applies to AMD drivers at least, which I read about on phoronix.

---

### Post by Brandon.Viking on 2009-03-09
Are there any updates to this thread?? I have also noticed that Blender is SLOW! while running it under Compiz. Any ideas as to what the slowness is caused by??

Regards,
Brandon.:popcorn:

EDIT: only in full screen, if you run Blender in Windowed mode but smaller than the screen size (blender -w p 0 0 800 600) Im running my screen at 1680 x 1050 this then drew the windowed version. The option for blender (windowed) off of the menu didnt work.
Still what difference does a window verses full screen make??

---

