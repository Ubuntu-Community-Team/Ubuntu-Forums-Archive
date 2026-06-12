---
title: "Window width truncated"
date: 2013-07-05
forum: General Help
---

### Post by lordbah on 2013-07-05
I don't think this is a wine issue, I think it's a window manager issue. I had Ubuntu 12.04 64-bit with wine 1.5 running a game at 1900x1050 (my display is 2048x1152). Upgraded to 13.04 and now the window is truncated to half the width of the screen. I can show part of the problem with xeyes

xeyes -geometry 1240x999 gives me a window about half the width of my screen and most of the height. 
xeyes -geometry 1640x999 gives me the exact same size window. 
xeyes -geometry 1240x1000 gives me a window which is maximized.

If I was able to get the wine window to maximize, I wouldn't mind so much, but I haven't been able to make that happen.

Where do I find switches for this kind of behavior? Basically I want the computer to do what the hell I tell it, not "help" me by changing the size of my windows. (in spite of which I am still running unity - I did find the place to turn off "if you touch anywhere near the bottom of the screen I'm going to vertically maximize this window, because what else could you possibly want? surely you don't just want to bring the window to the front")

---

### Post by lordbah on 2013-07-05
To defeat the width truncation I had to go into CCSM, Window Management, and uncheck Place Windows. It isn't enough to change the Placement Mode - any mode results in the window width being truncated. Unfortunately this exposes a new issue, the window gets placed with origin on my second monitor, straddling across to the main monitor. The place to address this would appear to be the Fixed Window Placement tab of the very Place Windows plugin which I just had to disable.

There's another plugin called Window Rules which looks like it should be able to control window size. Unfortunately ccsm crashed while trying to grab the window title. *sigh*

---

### Post by lordbah on 2013-07-06
Window Rules by matching window title is working to set the window size. Using the same title matching for Fixed Window Placement in Place Windows is not working.

---

