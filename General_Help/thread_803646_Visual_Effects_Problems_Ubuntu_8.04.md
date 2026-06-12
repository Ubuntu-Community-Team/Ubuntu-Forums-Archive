---
title: "Visual Effects Problems Ubuntu 8.04"
date: 2008-05-22
forum: General Help
---

### Post by glich509 on 2008-05-22
In 7.10 I was able to have all the compiz custom effects working with no problem.  Then just yesterday I upgraded to 8.04 and now i cannot select the custom effects option in the appearance tab.  I did get it to work using the xserver-xgl but that also caused an immense slow down of everything.  I removed the xgl package and speed is back up but of course no effects.  When I try to select custom (or extra or normal) it says desktop effects could not be enabled.  I have an ATI Radeon Mobility 7500 card.  Any help would be greatly appreciated.

---

### Post by Forlong on 2008-05-22
Try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by raafaell on 2008-05-22
See if your Video Card is working properly.

> System -> Administration -> Hardware Drivers

---

### Post by glich509 on 2008-05-22
I tried the Compiz-Check and it said that my card was blacklisted but gave me the option to bypass the blacklist if i was able to run compiz sucessfully in 7.10.  I bypassed it and the effects now work but my system is running slowly again.  Are there any configuration options or anything within compiz that can help with that?

And as far as checking if my device is working properly by going into system->administration->Hardware Drivers it says that no proprietary drivers are in use.  Is that a problem?

---

### Post by Forlong on 2008-05-22
> **glich509 said:**
> the effects now work but my system is running slowly again.  Are there any configuration options or anything within compiz that can help with that?
Do you have Xgl installed (Compiz-Check should have told you about that as well)?
> **glich509 said:**
> And as far as checking if my device is working properly by going into system->administration->Hardware Drivers it says that no proprietary drivers are in use.  Is that a problem?
No.

---

### Post by glich509 on 2008-05-22
Here is what compiz-check says for me now after bypassing the black list.
I dont see anything about xgl...

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-05-22
So you mean it's fine when disabling Compiz but when you enable it, the "system is running slowly"?

May I aks what you mean by that?

---

### Post by glich509 on 2008-05-22
By running slowly I mean that things such as dragging windows, opening new windows, and loading web pages just are not fluid and seem to lag.  Also once in a while it'll hang up and ill have to restart my session.

---

### Post by clothing optional on 2008-07-09
Just had to chime in, since i'm in the same predicament...
i ran compiz-check and got:
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

:::::
now when i enable the "custom" setting under appearance preferences, it instantly goes white and when i return to previous settings i can't enable any of the visual effects without the same result.

any ideas/advice about what i'm doing wrong?

i've installed compiz and emerald, as well as SCCSM...

i can't figure this out, and it is making me want to jump out of my window.

---

