---
title: "compiz, beryl, and what do i do?"
date: 2007-08-01
forum: General Help
---

### Post by HPCE_Larry on 2007-08-01
I'm trying to make everything look all nice and shiny as seen in the various pictures of compiz. However, i have no idea how to do that. I enabled desktop effects, only to have the bar with the min/max/close buttons dissapear. 

Even so, there are only two options on the desktop effects and compiz is supposed to have way more than that. Help please, its midnight and this is driving me nuts.

Lastly, if i make all this work, is this compatable with various GDM/icon themes or does it only work with its own.

---

### Post by Malh on 2007-08-02
All of the beryl options can be found at the beryl settings manager.  As for your bar, I think you can find your answer in the archives--> [http://ubuntuforums.org/archive/index.php/t-307530.html](http://ubuntuforums.org/archive/index.php/t-307530.html) .

---

### Post by HPCE_Larry on 2007-08-02
None of the changes that occur in the beryl settings manager apear to actually happen. The only thing that ever has any effect is desktop effects in System > Preferences > Desktop effects. And those remove the bar.

In that thread you pointed out, the suggested typing metacity -- replace. that got the bar back, but it also disabled all the effects, which sorta kills the point.

i'm running an 8800gts 320mb if that makes any difference.

---

### Post by dabl on 2007-08-02
First question is, do you have glx enabled in your video driver?  To find out, open a console window and enter ```
glxgears
```  You should get a graphic and a report of the frames-per-second performance in the console.

Next question is, is Beryl happy with your configuration?  To find out, in the console window type ```
beryl
``` or maybe it is ```
beryl-manager
``` (sorry, it's been awhile).  This will start an "audit" of your video setup, and it needs to run free of error messages.

HTH  :)

---

### Post by HPCE_Larry on 2007-08-02
I got this when i typed beryl (in addition to other stuff saying pass)
```
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
Segmentation fault (core dumped)

```

Is that an error, and what do i do about it. Everything else said passed.

---

### Post by HPCE_Larry on 2007-08-02
ok quick update. I enabled desktop effects and this time I actually have my bar. However, while virtually all of the effects are enabled in the beryl settings manager, only the jello window thing actually occurs. What needs to be done to enable the other ones?

---

### Post by HPCE_Larry on 2007-08-03
sorry for the tripple post, but i've discovered something else. I've managed to get the compiz manager (not sure how) and it actually has an effect on whats viewed in the screen. The cubed desktops, etc. However the beyrl manager does nothing. What gives? And is there a way to consolodate them?

---

