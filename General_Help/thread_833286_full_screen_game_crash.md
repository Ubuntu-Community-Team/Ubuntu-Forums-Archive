---
title: "full screen game crash"
date: 2008-06-18
forum: General Help
---

### Post by constantgamer247 on 2008-06-18
some times when I am playing urban terror (FPS) or other games on my linux box (it has a 64MB nvidia GPU and 1GB of ram) the games just warp out of full screen.  One min I am owning noob perfectly fine, the next its kind of frozen.  The game leaves full screen and becomes stuck in a small box in the top left corner of the screen.  It is still running, but I cant find the mouse to click back on the window.

The only solution so far is to crtl+ald+delete (that takes me back to the login window)
then I have to restart my game, this is very frustrating

plz help
gabe

oh and the computer is running ubuntu 7.10

---

### Post by Gerafin on 2008-10-12
I had this exact same problem. Here's why it's doing this.

When in a fullscreen game, the mouse movements and key presses are not registered by Ubuntu, but only by the game. So, eventually, your screen saver will want to start. As soon as the screen starts to dim, signalling the impending start-up of the screensaver, the game will no longer have control over your mouse and Ubuntu will recognize you moving your mouse. This will stop the screensaver, but crash the game. The simple solution is to turn off your screensaver before playing any games.

---

### Post by SVEN1 on 2009-02-15
Had the same problem last night, after about 20 minutes of play. I thought I was loosing internet connection. After about 2 hours of playing. Noticed that it happens generally when I sit ready to snipe. That'a about time the screen saver would start. Figured if I move the mouse just as the screen starts to want to go into screen saver or move the center mouse wheel. It will come back to the game even when the full size screen goes small. Only worked about 40% of the time.

Glad to have  found this post, next time playing I will turn off the screen saver.

---

