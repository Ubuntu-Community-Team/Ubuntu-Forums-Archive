---
title: "No Firefox window borders"
date: 2008-06-16
forum: General Help
---

### Post by md389 on 2008-06-16
Hey Fellas, 
    Recently, my firefox window borders have completely disappeared. I have tried restarting the comp and reinstalling firefox, but it hasn't helped. Furthermore, when I press alt-tab to get all the window previews to come up, the computer lags horribly and only shows a black screen when the firefox window is selected. Please help!

Mainak

PS: Im on hardy heron

---

### Post by rune0077 on 2008-06-16
Perhaps you are just running Firefox in fullscreen? Try pressing F11 and see if that gets it back in normal windowed mode.

---

### Post by tgrimley on 2008-06-16
Is it only firefox that is lacking borders or all applications?  If it's everything you just need to reload the window decorator..

---

### Post by md389 on 2008-06-16
No its definitely not in full screen mode. Thats what I originally thought the problem was. I can actually go view => fullscreen and switch it to fullscreen mode. Also, it is just firefox that has this problem. Opera and all other programs are working just fine. 

='[

---

### Post by rune0077 on 2008-06-16
That's weird. If you are using Compiz, try launching the settings-manager, go to "Window Decoration" and see what it says under Decoration windows. It should say "any".

EDIT: try running

> compiz --replace

see what happens.

---

### Post by md389 on 2008-06-16
I don't think I manually installed compiz. I'm on hardy so I think desktop effects come standard. Should compiz --replace still work?

---

### Post by rune0077 on 2008-06-16
Yeah the command should still work. Also, from Synaptic, search for compiz-config-settings-manager and install it (you'll want it anyways, since it makes Compiz much more configurable).

---

### Post by md389 on 2008-06-16
Ok so I tried compiz --replace. No results. Also compizconfig settings manager is already installed, but I don't know how to access it. Thanks for your help so far.

---

### Post by rune0077 on 2008-06-16
> **md389 said:**
> Ok so I tried compiz --replace. No results. Also compizconfig settings manager is already installed, but I don't know how to access it. Thanks for your help so far.

System > Preferences > Advanced Desktop Effects Settings.

Another thing you can try is to turn Compiz off and let Metacity do the decorations:

```
metacity --replace
```

This will at least tell us if the problem is related to Compiz (if you get windows borders with Metacity, then Compiz is likely the culprit).

You can get back to Compiz again with:

```
compiz --replace
```

---

### Post by md389 on 2008-06-17
Ok so I did metacity --replace, and my firefox window borders are back! Thanks! But there has to be a downside doesn't there? I mean what's wrong with compiz? And why was it only affecting firefox? Thanks so much in the meanwhile.

---

### Post by rune0077 on 2008-06-17
You shouldn't consider the problem fixed. When you did "metacity --replace" you stopped using Compiz (it was replaced by Metacity, so all your other Compiz-settings are probably also disabled now.

But now at least you know that Compiz is the problem. You can get Compiz up and running again with "compiz --replace" (or by restarting), once you've done this, try running firefox from a terminal:

```
firefox
```

Look for any kind of error output in the terminal when it loads firefox (or try to post the result here).

Other than that, you should still run CCSM as mentioned in previous post and check if you have set some specific rules for firefox.

---

### Post by monoufo on 2008-06-17
I have the same problem.  most window borders are fine.  firefox is always messed up.  I think some others are sometimes messed up.  I am dependent on compiz and will not turn it off for long periods of time.  I think it started around the time I enabled dual monitor mode.

---

### Post by peterdm on 2008-06-28
I've got the exact same problem since recent updates: firefox has no window decorations with compiz (using recent nvidia gfx drivers) :( Other apps are not affected. I've double-checked my compiz settings and they are fine. I found a workaround though: hitting F11 twice (once to get into fullscreen mode and once to get out of it again) makes the decorations go back to normal.

Peter

---

### Post by uababy on 2008-07-01
I got the windows decoration to stop disappearing.  I was having the same problem and was able to work around it by hitting F11 twice, though that was pretty lame.  

What I ended up doing is opened the Compiz Config Settings Manager, and edited the Decoration windows to be 
[COLOR="RoyalBlue"]
(any) | class=Firefox[/COLOR]

This basically says apply the decoration windows to any window or to the firefox windows.  Seems funny that I would have to do that, but it worked like a charm.  Haven't seen the issue since.

---

### Post by ubergunner86 on 2009-10-22
Hey this worked for me:

By default, the screen was left on maximize to start up with.

Un-maximize (restore) the firefox window and resize the window to a smaller size, so that it fills maybe half of the screen.

Close the window.

Re-open Firefox (as it should start un-maximized now).

Maximize (if desired).  And when you close and re-open it should open to default maximize size.

If you can't get the window to restore in the first place, try pressing F11 to make it fullscreen, then f11 again to make it UN-fullscreen.

If all of that still doesn't work, do the metacity --replace trick beforehand and then proceed with the steps above.  

Also, it could be compiz or even emerald.  This should be solved just by typing --replace for any of the programs.  

I hope this works for you all, as it worked for me!   :P


***Running***

Emerald Theme Manager
Compiz Fusion
Mozilla Firefox

---

