---
title: "Brightness Prolblems in Ubuntu Linux"
date: 2008-01-22
forum: General Help
---

### Post by KillaW0lf04 on 2008-01-22
Hey guys, i just recently decided to change from the disaster that is vista to ubuntu linux. I have to say so far im very impressed at the quality achieved from an open source program and that i dont see how im going to ever use vista again except for gaming maybe (I have it on dual boot).

Now down to my problem.....The brightness scroller for my laptop causes "flickering" as in at 100% its full brightness 90% lowest 80% highest etc ie its alternating between the two completely opposite levels. This is particularly annoying (btw this also happens when the screen dims from idle time- it flickers all the way to 0% which is lowest at least).

Does anyone know what i can do to fix this? Or has anyone had any similiar problems? Im running on a MSI GX600 laptop if that helps at all....

Thanks in advance for any help
Mike

---

### Post by KillaW0lf04 on 2008-01-22
anyone??

---

### Post by Lord Illidan on 2008-01-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Hi, and welcome to the forums.

I believe this may be related to : [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833)

---

### Post by rosegarden78 on 2008-01-22
Yeah you need to try this first:

1) Make new text file and type:

#!/bin/sh
xgamma -gamma 0.75

and save it as GammaC-down.  Right click file and make executable.  Goto Autostarted Programs in Settings and add this item: bash /path/to/script/GammaC-down

Gamma correction of 0.75 works best on a standard 15" LCD laptop panel at 86 ppi.  you may also add the bash command to a keyboard shortcut for ctrl-up and ctrl-down arrows.  Just use settings of -gamma 1.0 for high brightness and 0.75 for low brightness in the scripts.  Name the other script GammaC-up.

---

### Post by Lord Illidan on 2008-01-22
Gamma and brightness are not the same. The brightness controls should influence your LCD backlight. Try putting xgamma -gamma 0.1 (the lowest setting possible.) The backlight is still on. Thus, battery usage remains the same.

---

### Post by KillaW0lf04 on 2008-01-22
it works, but its deffinatly not the solution. Changing the gamma levels in the screen isnt the same as changing the backlight intensity. (i changed back to a gamma level of 1.0 because 0.75 looks pretty bad)

---

### Post by rosegarden78 on 2008-01-22
Hmmm....interesting.  I guess we all need a little program like xgamma for brightness so we can write a shell script for brightness, too:  For me my black screen had dark gray stripes at gamma 1 so changing it to 0.75 gave me a solid black black regardless of back light.  Your photos will look best if you get your gamma set for pure black without faint stripes.  Most affects Dell 15" LCD Panels.

---

### Post by KillaW0lf04 on 2008-01-23
Ive been playing around with every setting to do with backlight that i can think of and still nothing :/ Is there no fix to this? =S

---

### Post by KillaW0lf04 on 2008-01-23
Is there a way of changing the brightness from the terminal? Maybe we can make some kidn fo script to change the backlight proporly....

---

