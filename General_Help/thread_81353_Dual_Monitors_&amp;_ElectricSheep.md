---
title: "Dual Monitors &amp; ElectricSheep"
date: 2005-10-24
forum: General Help
---

### Post by kscurloc on 2005-10-24
Was wondering if anyone had any weird problems when using Dual Monitors and the ElectricSheep screensaver.  All other screensavers seems to work just fine, but with Sheep each monitor displays something differnet.  

For example, one monitor displays only in it the top left corner of the screen.  While the other screen has a full screen display, but it only shows 1/4 of the complete screen saver itself.  Sounds a bit confusing perhaps... 

I do have Sheep setup to do a "Zoom".  Tried with and without that setting, did roughly the same thing.

Any ideas/suggestion?  Thanks in advance!

---

### Post by brian g on 2005-11-06
wow.. you actually got ES to actually work and download sheep?
i have 2.6.2 from the breezy install but it just sits there doing nothing.

---

### Post by plong0 on 2006-09-29
Brian, I had the same problem... I could run electricsheep from the commandline just fine, but when I tried it as my screensaver, it sat black.  I fixed it by switching from gnome-screensaver to xscreensaver.  Easy HOWTO on that: [http://www.ubuntuforums.org/showthread.php?t=195557]("http://www.ubuntuforums.org/showthread.php?t=195557")

But with having it run on two monitors there's new problems... It seems xscreensaver runs a seperate instance of the screensaver for each monitor... electrichsheep doesn't like it and displays an error message.  I fixed this by downloading the es source code and finding the line that prints the message (in electricsheep.c) and commenting it out, recompiling, and replacing the existing /usr/bin/electricsheep (back it up of course) with my newly compiled electricsheep

So now I have electricsheep running on both monitors, sometimes they display from different sheep, sometimes the same one; but I don't mind, I like looking at all the sheep... they all so sexy :)
The only remaining problem now is that on both monitors it displays the left half of the screensaver (my desktop stretches across both) ... and I'd like my right monitor to display the right half of it (even of a different sheep would make me happy)  so I'm going to try to modify the code to divide the full screensize in half and either have it display a full sheep on each monitor OR have it display the left half on one side and right half (of a potentially different sheep) on the other.
I will keep you posted on the progress

---

### Post by plong0 on 2006-09-29
and sorry ksurloc, I am not sure about your problem... I was having something similar where I'd just have a small box playing the sheep in the top left corner of each screen... I fixed it by adding the --root 1 --zoom 1 parameters ... Now I have the result of the left half of a stretched sheep displayed on both monitors :P  And I'm working on that, but for now 2 full screen half sheep are better than no sheep I say :D

There was also some xscreensaver bug where you would have to set the zoom option. Then in the screensaver list, arrow key up to Drift and back down to Electricsheep for it to work properly.. very strange, but could make the difference?

---

### Post by capaci on 2007-05-19
hey...did you ever get one sheep to span both screens? it's kind of annoying just seeing the left half.

---

### Post by wrongo on 2007-05-19
Had two monitors working in Kubuntu (broke xserver, installed Ubuntu) - it was so easy (system, monitors, presto) - but how in UBUNTU Feisty Fawn???

---

