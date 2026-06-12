---
title: "[SOLVED] Black Screen on Boot"
date: 2008-03-06
forum: General Help
---

### Post by 3uph0riac on 2008-03-06
I was trying to install the ATI restricted drivers for my Radeon x1950gt Super (AGP) and ended up needing to do it the manual way since I wasn't able to successfully complete the simple/depository way. 

I was nearly finished and restarted because I needed to. Now when I boot, everything appears to be fine and the ubuntu loading screen displays then immediately shows a black screen... no cursor or anything, just black. I can get into the recovery mode command line without a problem.

I was hoping someone could tell me how to either reset the graphics setup to whatever the default is, or how to complete the restricted driver setup solely on command line.

If it is useful, I am writing this using the live cd and I believe fglrx (correct letters?) was disabled through the process I was following.

*Any help would be much appreciated. Sorry if my post is a long read.*

---

### Post by taurus on 2008-03-06
From the recovery mode, reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by 3uph0riac on 2008-03-06
Hmm, that seemed to have remedied my graphics problem... I am now able to run the native resolution of my LCD without any problems, using the vesa driver. 

Would there be any reason why my sound wouldn't be working as a result of this? Personally I can't see how the graphics fix would be related to the sound but I'm only new to ubuntu and its the only change I have recently made.

Also, is there any way I can have my cake and eat it too? That is, to have the proper driver for my card and fully utilise it without any problems?

---

### Post by 3uph0riac on 2008-03-06
Nevermind, I ran alsamixer in terminal and it seems a channel was muted, so i un-muted it by pressimg m.

---

