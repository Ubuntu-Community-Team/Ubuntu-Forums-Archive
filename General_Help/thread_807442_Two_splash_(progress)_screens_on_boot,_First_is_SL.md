---
title: "Two splash (progress) screens on boot, First is SLOW"
date: 2008-05-25
forum: General Help
---

### Post by BandD on 2008-05-25
I didn't have two different splash screens in Gutsy.  But in Hardy I have one the appears first with a scrolling (think pong) shorter bar that tries to move back and forth and a second "normal" splash screen where the bar "grows" across the screen from the left (similar to what you see on the LiveCD).

The problem seems to be with the first screen.  It takes more than 30 seconds to get through this screen and drastically increases my boot time.  It seems to hang as it approaches the right side of the progress bar in it's pong like routine.  It gently glides toward the right side.  Once it is about 85% of the way there it then slowly jerks it's way to the right side, inches back toward the left, then takes off again like normal...then the "normal' splash screen loads and it flies through the boot process just like it did in Gutsy.

Anyone have an idea what this fist splash screen is about?

---

### Post by BandD on 2008-05-26
It seems to be a problem with splash.  

I tried booting with "quiet" and "splash" removed from the boot options line (at grub, pressed "e", selected "kernel" line, removed "quiet" and "splash", enter, the pressed "b") and it flew.  It took less than 60 seconds from grub to desktop.  With splash it takes closer to 1:40.  (In Gutsy with splash it took less than a minute.)

As all the lines were flying by, there wasn't an obvious 'lag' point like I had seen in the first of the two splash screens.  So I'm not really sure what is happenning here.

---

### Post by BandD on 2008-05-27
AS of yesterday, I installed the updated 2.6.24-17 Kernel, and my boot times have drasctically improved.  Now I'm down to right around 60 senconds WITH Splash.  So I suppose something in 2.6.24-16 just didn't play nice with my system or something...

---

