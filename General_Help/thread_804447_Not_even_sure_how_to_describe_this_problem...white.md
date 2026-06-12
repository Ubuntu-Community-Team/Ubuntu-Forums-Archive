---
title: "Not even sure how to describe this problem...whiteout screen?"
date: 2008-05-23
forum: General Help
---

### Post by Donalb on 2008-05-23
OK, bear with me if I don't describe this accurately...

Recent (<3 weeks) Hardy/full time 'buntu user.
I've noticed when I'm away from the system fro a while and return and switch on the monitor, the screen/system acts very strange.

Switching on the monitor <may>  display a barely visible image of the current desktop before the screen "whites-out". By which I mean the screen goes quickly (about 1/2 seconds) almost white, like piece of paper burning out to the edges from the centre. Some faint vertical lines may then be visible, which may change on a key press.
I say may because there are slight changes each time, sometimes the desktop may become faintly visible for a fraction of a second on a key press.

It will take switching on and off the monitor from 2 to 10 times before I return to the normal desktop environment. Commom keys pressed seems to have no effect (<enter>,<ctrl-alt-del>,<esc>,<space>, <del>, <backspace>, etc) .

In settings, no screen saver is selected, and Power Management options are off. Compiz is off also. 
I still have a dual boot system but have never seen a similar issue in XP, so it's not the monitor I guess. 

I'm running Hardy, on a 3 yo Dell D600 Latitude lappy, with ATI Radeon 9000, in a docking station, with a generic 19" LCD. 


Sorry for the confusing description, best I could do. Obv. I can't do a snapshot....


Regards
Donal

---

### Post by ajgreeny on 2008-05-23
Seeing that you have an ati 9000 card for graphics, I think the most likely cause of your problem is the graphics driver and minor (relatively) problems wuth that.  If you're not aware of the situation, ati cards tend to be a bit of a problem with linux in general.  I have an ati 9200SE card which luckily seems to be one of the best supported by the ati/radeon open source driver, but there are still occasional glitches with strange things happening, particularly when I have compiz running.

Just to test the theory, try running without compiz, if you use it normally, and see if things improve.  There's a great script available to turn compiz on and off [here]("http://forlong.blogage.de/article/pages/Compiz-Switch")

---

