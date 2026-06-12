---
title: "Firefox window opens but does not load after upgrade"
date: 2015-08-13
forum: General Help
---

### Post by rdh61 on 2015-08-13
Hi,

Since yesterday Firefox (40.0+build4-0ubuntu0.14.04.1) opens but does not load properly. I can see the name of my homepage at the top with the Firefox logo on the right and the - + x buttons on the right. Below that nothing, no address bar, no buttons, toolbars, tabs, pages - just a blank screen. I am almost sure this began to happen after a package upgrade, but no Firefox upgrades are listed in the history. (And I am absolutely certain there have been some recent package upgrades although none are listed in the history!) I have tried removing and reinstalling Firefox. I have tried rebooting. How can I restore Firefox, please?

Thank you.

---

### Post by monkeybrain20122 on 2015-08-13
Just as a guess try to do this: type about:config in the url bar, click "I'll be careful, I promise", then search for "layers.offmainthreadedcomposition.enabled" and set it to false, then restart FF.

---

### Post by rdh61 on 2015-08-13
Thanks but can't do that: no url bar!

---

### Post by nerdtron on 2015-08-13
Try running firefox in safe mode, from the terminal.
```
 firefox -safe-mode
```

Or if you want to reset your firefox for a fresh profile, in you home folder, show hidden files. You see the .mozilla folder. Move (or rename it) to some other place. Then launching firefox again will make it look like a fresh install.

---

### Post by monkeybrain20122 on 2015-08-13
> **rdh61 said:**
> Thanks but can't do that: no url bar!

The url bar is just the place where you enter an internet sites' address like [https://www](https://www).....

---

### Post by nerdtron on 2015-08-13
> **monkeybrain20122 said:**
> The url bar is just the place where you enter an internet sites' address like [https://www](https://www).....

His Firefox is blank. Almost just like a floating window only with nothing on it. 
> I can see the name of my homepage at the top with the Firefox logo on  the right and the - + x buttons on the right. Below that nothing, no  address bar, no buttons, toolbars, tabs, pages - just a blank screen. 

---

### Post by rdh61 on 2015-08-13
Thanks. Safe mode resulted in the same behaviour and gave:

```
robert@robert-P4i65GV:~$ firefox -safe-mode


(process:3508): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(firefox:3508): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(firefox:3508): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(firefox:3508): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(firefox:3508): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised



```


So I deleted my profile and Firefox then opened as a fresh install as you suggested. But with the url bar greyed out so I couldn't see what I was writing in it. I found a suggestion that the solution to that was to change the setting "gfx.xrender.enabled" (in about:config) to "false". I did this and then restarted Firefox, with the result that the whole window was blank as before. I know I had the greyed out url bar problem some time before. So I am guessing I used the above "fix", which worked then, but with this upgraded package produces my current problem behaviour of no working window at all.

A short but I think important rant: Am I the only one who is constantly bugged by this software developers' neurosis (Mozilla's in this case but the disease is generalised) of constantly "improving" things that worked perfectly well, only to bugger them up, making ordinary users waste hours of valuable time looking for fixes?

Back to practicalities, does some kind person have a quick fix for the greyed out url bar? If not I'll start a new thread about that as the specific problem of this thread is I suppose to be considered "solved".

Thanks again.


> **nerdtron said:**
> Try running firefox in safe mode, from the terminal.
```
 firefox -safe-mode
```

Or if you want to reset your firefox for a fresh profile, in you home folder, show hidden files. You see the .mozilla folder. Move (or rename it) to some other place. Then launching firefox again will make it look like a fresh install.

---

### Post by vbm on 2015-08-15
Hi, there is no need to delete your profile or fresh installs:

+ go to your profile on ~/.mozilla/firefox/*something*.default/
+ edit prefs.js, find the 'gfx.xrender.enabled' entry and replace 'false' with 'true'
+ start firefox, if the address bar is funky, install the FXchrome theme

found the solution here: [https://support.mozilla.org/en-US/questions/1077576](https://support.mozilla.org/en-US/questions/1077576)

---

### Post by estrait on 2015-08-15
Ok, after the update to 40.0 a few days ago I'm suddenly having problems with the screen repainting. After I minimize or send to background with another window then bring back to foreground the top menu half area doesnt repaint itself. I'm left with no menu, tabs, bookmark menu and all other controls are gone. If I move my mouse over top the area where they should be they will redraw but only if I hit each item with the mouse. Also if I maximize the window it redraws fine and then minimize back to normal the same. But a short time later the same thing again. Gonna try the "search for "layers.offmainthread_ed_composition.enabled" and set it to false, then restart FF" in the about:config which should be `layers.offmainthreadcomposition.enabled`, thread not threaded. And yes, I've tried SafeMode and a clean profile with same results. Even reloaded FF40 fresh. So far 30 minutes and all is good.

---

### Post by estrait on 2015-08-15
So far, so good. Still displaying correctly.

---

### Post by v3.xx on 2015-08-15
> A short but I think important rant: Am I the only one who is constantly  bugged by this software developers' neurosis (Mozilla's in this case but  the disease is generalised) of constantly "improving" things that  worked perfectly well, only to bugger them up, making ordinary users  waste hours of valuable time looking for fixes?

This is why I switched to FF ESR.

[https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)

---

### Post by rdh61 on 2015-08-17
> **vbm said:**
> Hi, there is no need to delete your profile or fresh installs:

+ go to your profile on ~/.mozilla/firefox/*something*.default/
+ edit prefs.js, find the 'gfx.xrender.enabled' entry and replace 'false' with 'true'
+ start firefox, if the address bar is funky, install the FXchrome theme

found the solution here: [https://support.mozilla.org/en-US/questions/1077576](https://support.mozilla.org/en-US/questions/1077576)


Thanks. May come in useful another time.

---

### Post by rdh61 on 2015-08-17
> **v3.xx said:**
> This is why I switched to FF ESR.

[https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)


I'll check it out.

---

