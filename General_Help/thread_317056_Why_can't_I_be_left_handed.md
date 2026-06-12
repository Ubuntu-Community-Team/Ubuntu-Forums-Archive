---
title: "Why can't I be left handed??"
date: 2006-12-11
forum: General Help
---

### Post by jamespw on 2006-12-11
I'm very sorry if this has been answered before:
I'm using ubuntu on a laptop, and when i change buttons to left handed mode, the buttons work fine, but it assumes that when i touch with the touch pad, that it's a secondary click, instead of a primary click- so i cannot open apps using the touch pad!
I find this very annoying, any help would be greatly appreciated.
Also, will this be the same on KDE?

---

### Post by pay on 2006-12-11
Open up nautilus (file manager) and press Edit --> Preferences --> Behaviour and then change to Single click to activate items.

---

### Post by drphilngood on 2006-12-11
> **pay said:**
> Open up nautilus (file manager) and press Edit --> Preferences --> Behaviour and then change to Single click to activate items.

genius!  Good thinking, pay.

---

### Post by jamespw on 2006-12-12
I'm not sure if I worded it properly...
When I touch the touch-pad, it assumes it's a secondary click, as in a Right handed Right-Click. That clearer?

---

### Post by tweedledee on 2006-12-29
> **jamespw said:**
> I'm not sure if I worded it properly...
When I touch the touch-pad, it assumes it's a secondary click, as in a Right handed Right-Click. That clearer?

Try here: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441).

You MAY be able to remap your touchpad to produce a left-click using xte and/or xmodmap, IF xev produces a unique button event for that click (i.e., not the same as when you actually right-click a button).  However, I've found that using a left-handed mouse on a laptop produces undesirable side-effects with the built-in device, and have not found a really good solution yet.  My best so far is just to keep a link around to call xmodmap to switch between two modes quickly, so when I don't have a mouse connected I can quickly switch the built-in device to "normal" behavior.  However, it sounds like in your case you may not have an external mouse at all, so if remapping doesn't work I think you are stuck.

---

### Post by raul_ on 2006-12-29
I can swear that System->Preferences->Mouse has a "left handed mouse" option...doesn't it work with touchpad?

---

### Post by tweedledee on 2006-12-30
> **raul_ said:**
> I can swear that System->Preferences->Mouse has a "left handed mouse" option...doesn't it work with touchpad?

The issue is that the "left handed" behavior leads to odd behavior with the buttons and/or tapping on the touchpad.  Selecting left-handed just swaps the left- and right-click buttons, but that isn't always sufficient to generate a truly left-handed device.  For example, if the tapping mode of the touchpad maps to button 1, and button 1 is remapped to the "right-click" mode, then tapping on the touchapd is screwed up for left-handed use because it no longer works as a primary click.  With my laptop, which just has the eraser nub, the buttons get re-arranged in a completely useless fashion by selecting "left handed mouse," so I do all the remapping myself.  This appears to be a fundamental limitation in the way X handles the mouse.

---

### Post by ronaldv on 2008-06-29
No solution yet, I suppose?

I'm having the same problem.

---

### Post by slyn4ice on 2008-07-16
> **ronaldv said:**
> No solution yet, I suppose?

I'm having the same problem.

Me too! This makes the touchpad entirely unusable without changing settings back to right-handed mode. Why hasn't this been addressed before? No lefties in the developers? Remember lefties make for at least 10% of the general population ... that's a lot of pissed lefty laptop-owners :)

It just seems like you put the left-hand switch button just to be politically correct hehe ...  i mean if you put it - make sure it actually works with more than one tracking device ...

aanyways

---

### Post by DirtDawg on 2008-07-16
You all may want to check out gsynaptics. Synaptics (not the same as *Synaptic* the package manager) is used to adjust touchpad behavior so, for example, one can set a two finger tap as right mouse button. Gsynaptics is Synaptics with a Gnome gui. I'm not on my laptop on the moment, so I'm not sure it will do what you need, but maybe you can use it to fix your issues.

Installing it is slightly convoluted as you have to add a line under "Input Device" in your xorg.conf file before you install. Luckily, it's pretty simple and there are some straightforward [instructions here]("https://help.ubuntu.com/community/SynapticsTouchpad#Configuration%20with%20a%20Graphical%20Interface"), under the "Enabling SHMConfig" link.

If I understand your problem correctly, hopefully this will help.

EDIT: Good lord, I just realized how old the OP is! Good luck :KS

---

### Post by slyn4ice on 2008-07-16
> **DirtDawg said:**
> You all may want to check out gsynaptics. Synaptics (not the same as *Synaptic* the package manager) is used to adjust touchpad behavior so, for example, one can set a two finger tap as right mouse button. Gsynaptics is Synaptics with a Gnome gui. I'm not on my laptop on the moment, so I'm not sure it will do what you need, but maybe you can use it to fix your issues.

Installing it is slightly convoluted as you have to add a line under "Input Device" in your xorg.conf file before you install. Luckily, it's pretty simple and there are some straightforward [instructions here]("https://help.ubuntu.com/community/SynapticsTouchpad#Configuration%20with%20a%20Graphical%20Interface"), under the "Enabling SHMConfig" link.

If I understand your problem correctly, hopefully this will help.

EDIT: Good lord, I just realized how old the OP is! Good luck :KS

Gsynaptics is what i am currently using and it is not giving any options to ameliorate the problem ;) Bump. But don't worry about how old the post is - lefties are not going nowhere :D

---

### Post by DirtDawg on 2008-07-16
> **slyn4ice said:**
> Gsynaptics is what i am currently using and it is not giving any options to ameliorate the problem ;) Bump. But don't worry about how old the post is - lefties are not going nowhere :D

:lolflag: Good luck.

---

