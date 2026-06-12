---
title: "Can't use CTRL mousewheel to zoom in firefox"
date: 2012-12-08
forum: General Help
---

### Post by hawthornso23 on 2012-12-08
It stopped working a while back which was annoying. It has become more annoying as time has passed. I've now reached the point where I have GOT to fix this because it is driving me nuts. CTRL + still works, but since I'm on a laptop this requires a 3 key combination. That is because I have no numpad and need a shift key or function key to access the symbol + which means I  need to stare at the keyboard to find the three keys needed to do it. CTRL mousewheel was very natural and I've been using this since forever. 

I am not sure of the cause but suspect something is going on with the CTRL key. Several other things that use control also seem to have broken recently. Some of the compiz functions using control have started glitching for example. I've also noticed a new cute but useless animation consisting of blue concentric circles whenever I hold and release the CTRL key and I wonder if this isn't getting in the way of some of these functions.

I'm using 12.04

In firefox about:config I have 
mousewheel.with_control.action;3

---

### Post by hawthornso23 on 2012-12-08
OK - found it and fixed it.

Under Mouse preferences (of all things) there is a checkbox for "show position of pointer when control key is pressed". Unchecked it.

CTRL mousewheel now zooms again in firefox.
Compiz has also stopped glitching when using key combinations involving CTRL. 
[EDIT: Not all compiz functions stopped glitching - needed to turn off cube unfolding]

Obviously some incompatibility bugs here. Suggest more caution is needed when changing the function of keys on the keyboard to ensure that this doesn't interfere with other programs that might use the same key.

---

### Post by iamthefirstandthelast on 2013-02-08
Thanks man I appreciate this post as I was having the exact same problem and searching for some solution. Then when I found out what was causing it I was gutted I couldn't use that  "show position of pointer when control key is pressed" option anymore. So instead of unchecking it, I tried it one more time and it worked!! 

How did I do it?

On the Firefox screen, Press CTRL, then just click once on the screen. This basically disables that  "show position of pointer when control key is pressed" option momentarily and Firefox understands that you are trying to zoom from then on. Good thing is,  "show position of pointer when control key is pressed" will still work once you release CTRL key!

Best of both worlds but a bit of annoyance still. On Windows, I think the moment you press CTRL it showed the position of pointer straightway while in Ubunto you have to release it to work in the first place. So basically in Windows, pressing CTRL key will immediately initiate "show position" then any command to follow. But in Ubuntu, it has to be interrupted momentarily by clicking on a screen.

Cheers

---

