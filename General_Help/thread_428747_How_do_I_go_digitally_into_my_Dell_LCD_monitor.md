---
title: "How do I go digitally into my Dell LCD monitor?"
date: 2007-04-30
forum: General Help
---

### Post by mjpatey on 2007-04-30
Hello,

I have a desktop running Feisty, with a PNY nVidia GeForce 6200, and a Dell 1801FP LCD monitor. I just noticed that both my video card and monitor have digital connections, and that I have a digital cable! So I decided to remove the analog cable, and connect the digital one.

Unfortunately, when I do, the monitor stays in the "Analog" input mode with its built-in screensaver floating around the screen, and hitting buttons on the monitor does absolutely nothing.

So I reconnect the analog cable. From the monitor I get:

"Monitor is in Power Save mode. Please hit a key on the keyboard or move the mouse to resume..."

...or something to that effect.  No mouse or keyboard activity will actually snap it out of it, though.  Only after a hard reboot am I able to get even the analog input working again, with seemingly no hope for digital.

So I'm obviously missing something if I want to get digital working. Do I need some kind of driver? Some tweak to xorg.conf to tell Ubuntu that I want to use the digital output?

Any help would be greatly appreciated!

-Mark

---

### Post by robrmd9 on 2007-04-30
I don't think you need to tweak any settings in Ubuntu.  

Some Dell monitors have buttons that switch between the inputs (analog, digital etc) so you could look through your monitor's OSD and see if you find anything there.

---

### Post by mjpatey on 2007-04-30
Right, I tried that.  As I mentioned, the OSD simply stays in screensaver mode, and the buttons all do nothing.  Very odd.

Wait, stop the presses!  I just realized that I've been keeping my OSD locked (have a toddler)... I just unlocked it and will try this again.  I'll report back to say whether I was able to switch inputs this time...  :) 

-Mark

---

### Post by mjpatey on 2007-04-30
OK, I'm back...

With the OSD lock turned off, it did allow me to switch to digital mode finally, but the monitor still just threw up its "testing" screensaver.

30 minutes later I returned to the machine (did I mention I have a toddler?) and found that it was in Analog mode again.  This time when I switched to Digital, it worked!  No clue why, except maybe it was finished "testing" whatever it was testing.

So now I have lovely, crisp, digital pixels!

-Mark

---

### Post by robrmd9 on 2007-04-30
Switching between video modes gets screwy sometimes, but DVI rocks! :)

---

