---
title: "Urgent- 64-bit broke, resolution low"
date: 2008-06-14
forum: General Help
---

### Post by LeoSolaris on 2008-06-14
Alright, after yesterday's upgrade I restarted, and much to my horror, compiz broke completely. Ok, I figured a little forum time was needed, so I found out that the 64-bit had an issue with the update, and to simply reinstall the nVidia drivers. 

After a little headache, I got the drivers reinstalled for the right kernel. (I had to clear out the two older ones.)

So the video card is working, I can enable compiz. The issue is it will not detect my Inspiron 1520's monitor. Neither the Screen Resolution or the recently installed nVidia xserver config worked. All it is giving me is CPT Monitor with a 600-480 at 50 Hz.

I am betting I can hand write the xorg file, but I'm not 100% sure what to put in it.

Leo

Edit 1:Alright, I did sudo dpkg-reconfigure -phigh xserver-xorg and it atleast fixed the resolution issue. Ok, now this is odd...   I can't turn the bold off...  what in the world?

Anyways, There still seem to be little graphical glitches, like the windows not moving smoothly with wobble windows, and the cursor not staying in the same place on the window when it moves.  

Add to that the touchpad's scroll area stopped worked. It worked even in low graphics mode, and it just stopped.Edit 2: hmmm...   The bold issue stopped, too.

---

### Post by Novega on 2008-06-14
Could the bold issue just be something associated with "Assitive Technologies" ?  I know my system defaults to having those options enabled whenever I make changes to my graphics related stuff?  

I'm pretty sure you probably already checked that, but just throwing it out there :p
I had the compiz problem yesterday too with a 64-bit system and a geForce 9 series card but I didn't experience any of the additional issues you've encountered so I can't be much help.

If nothing else, consider this a free bump :)

---

### Post by LeoSolaris on 2008-06-14
> **Novega said:**
> Could the bold issue just be something associated with "Assitive Technologies" ?  I know my system defaults to having those options enabled whenever I make changes to my graphics related stuff?  

I'm pretty sure you probably already checked that, but just throwing it out there :p
I had the compiz problem yesterday too with a 64-bit system and a geForce 9 series card but I didn't experience any of the additional issues you've encountered so I can't be much help.

If nothing else, consider this a free bump :)

Thanks!

Alright, the bold seems to be gone, and after playing with the xorg file, (I've decided that I really do love the fact that all of the graphical front ends have an accessible config file, marked improvement over Windows.) I copied over the entry the "reset" command created. Touchpad issue solved!

The small glitch slowly went away like it did last time...   Computer programing isn't supposed to DO that. It's not supposed to self correct. That's just kinda freaky. It happened that way before when I first installed 8.04, then again when I installed 64bit 8.04. I thought it was an update that solved the issue...  but this time, I had the issue, and it just went away after watching a couple of episodes of House on VLC.  

Seriously freaking weird.

Thanks for the free bump, and I think this dubious upgrade issue's sub-issue has been solved in my case. 

Check out my next new issue I discovered while trying to fix this in the next episode of "Leo's Laptop"

Leo

---

