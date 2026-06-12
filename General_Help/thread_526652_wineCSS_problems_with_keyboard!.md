---
title: "wine/CSS problems with keyboard!"
date: 2007-08-15
forum: General Help
---

### Post by doh224 on 2007-08-15
hi all! 

Couldn't find a Thread about this problem!
When I go into steam and into CSS or CS1.6 it all seems to work fine, but when i try to write a password to my server or try to change the numbers of "max players", it don't write anything. But well, I tried to enter the game anyway but the keyboard doesn't work there (ingame) either.?
So I could only get out of the game with ctrl+alt+backspace!
what to do? if anyone knows then please help. Thanks for any help given.

-doh

---

### Post by cogadh on 2007-08-16
If you have Wine configured to allow the window manager to control the windows, this keyboard focus problem goes away. However, if you are not using the latest version of Wine, then the system panels will still appear while the game is running in full screen. If the problem is still occurring with the latest version of Wine, then click on the "Stuff I've learned about Wine" link in my sig and scroll down to the "Advanced Stuff" section. It contains instructions on how to create a script to launch a game in a separate X session with no window manager at all, which will eliminate both the keyboard and panel problem (it also gives a significant performance boost).

---

