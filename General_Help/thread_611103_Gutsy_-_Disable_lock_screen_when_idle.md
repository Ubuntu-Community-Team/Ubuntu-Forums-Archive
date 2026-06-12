---
title: "Gutsy - Disable lock screen when idle"
date: 2007-11-12
forum: General Help
---

### Post by smug simian on 2007-11-12
Hi - 

I would like to totally disable the screen lock/password  prompt that shows up whenever my desktop is idle.

The problem occurs whenever I'm using "TVTime" to watch television using my capture card. Since I'm not moving the mouse, the screen will lock itself after a period of time (and interrupt whatever I'm watching)  


I tried disabling it from system^preferences^screensaver --- but that didn't work (still shows up) 
I tried disabling it from system^preferences^power settings (set to "never") --- that didn't work 
I was unable to find any settings for suppressing the screen saver/lock screen dialog under  tvtime's settings. 

Any ideas on where else I need to look, or what setting I need to change? :?

Thanks.

---

### Post by spier on 2007-11-12
There is one more place to tweak the screen lock configuration:

- run gconf-editor (from a Terminal or thru Alt+F2);
- in the left tree, select apps > gnome-power-manager > lock;
- uncheck the options you'll be free of. I unchecked blank_screen and use_screensaver_settings. 

HTH

---

### Post by smug simian on 2007-11-12
Hmmmm----doesn't seem to have worked. "use screen saver settings" was already unchecked when I reached that part of the tree. I unchecked everything else.....waited a while..... screen went black and  locked after 30 minutes.  

I guess it might help to know what exactly is happening, and what service  is controlling it.

---

