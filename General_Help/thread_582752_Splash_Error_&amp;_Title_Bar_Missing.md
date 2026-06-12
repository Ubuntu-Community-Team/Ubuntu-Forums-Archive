---
title: "Splash Error &amp; Title Bar Missing"
date: 2007-10-20
forum: General Help
---

### Post by whoeva on 2007-10-20
Hi everybody. Hope you're all enjoying the Gibbon :) Thank you all the devs and posters here who help people out ;)

I did a fresh install (previously was running Fiesty) but kept my home partition. I had the Splash program that would let me change my splash page upon logging in. The problem I have now is that this screen is still being shown and I have no way to stop/change it.

I've tried adding the Splash program again but when I go to run it nothing happens.
Anybody know a way to fix this?

Also I've used ```
gksudo nvidia-settings
``` to set up my TV on the 2nd screen and it all looks to be running beautifully with compiz-fusion effects enabled. With Beryl on Fiesty I had to disable it in order to use the TV but this seems to be working fine.

Howeva, the windows on the 2nd screen (TV) do not have the title bar with min, max and close buttons. It's not a big deal as I only use the TV to watch video on but if there is a way to fix it does anybody know?

While I'm at it, how do I change the colour of the screen after when I log in? I've already changed it in the login window but it still comes up as orange. Perhaps something to do with the Splash error?

Any help would be most appreciated.

---

### Post by whoeva on 2007-10-21
Well, I fixed the splash page. There was a file knocking around somewhere in the home folder. Once deleted I reinstalled splash manger and it operates successfully.

Still have orange border as I've read other people posting about. Nobody have a fix for this please?

I've got emerald running sweet but on the 2nd display there appears to be no window decorator. Surely there's a way to make it possible?

---

### Post by whoeva on 2007-10-26
Orange colour after log-in is now fixed. There's another thread somewhere that tells which file to modify to correct this.

Only have my missing windows decoration on the 2nd screen to fix now. I guess nobody knows anything about this?

---

### Post by woodsby on 2007-11-23
I had the same problem.  I figured out today if I add "emerald --screen 1" to my startup programs in System>Preferences>Sessions, that fixed the problem.  I named it "Window Decorator - Screen 1" so that it would be one of the last programs to run after login.

---

