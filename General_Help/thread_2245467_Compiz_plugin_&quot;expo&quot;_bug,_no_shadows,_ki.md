---
title: "Compiz plugin &quot;expo&quot; bug, no shadows, killall -9 compiz is the solution"
date: 2014-09-23
forum: General Help
---

### Post by bokiscout on 2014-09-23
Hi there,

I'm running fresh Ubuntu 14.04 minimal instalation, and there is a bug(or it is my fault) with "expo" plugin in compiz. Sometimes there is shadows around active worksapce but sometimes there is none after pressing "Super + W" key combination.

The bug is present right after boot, or it is not present at all. It can't apear while using the system under XY action/condition.

The solution is to run "killall -9 compiz" in terminal. After compiz is being restarted the bug is not present anymore, the shadows are visible as expected to be.

 
I'm not sure if this is bug or I broke something but still I'm looking for proper solution, at least automated method (script but I'm not able to write it) to run the comand at boot. 

So far I have changed the speed of minimize animation as described [here]("http://www.omgubuntu.co.uk/2012/10/how-to-speed-up-ubuntu-12-10-minimize-animation"), changed the expo animation duration, enabled experimetnal feature to minimize app by clicking icon on left panel, installed few pps (firefox, chrome, rhythmbox and nemo) and nvidia proprietery driver. At first I guess that it is my fault so I redo the instalation and carefully made one change at a time then reboot, made another change then reboot... I found out that this ocurs random after boot or it not apears at all.

---

### Post by deadflowr on 2014-09-24
Sounds more like a viewport switcher problem, or windows decoration problem or (because of the keybinding opf super +w) a scale problem.
I would go with window decorations, since shadows are one of it's features, and now that plugin for unity is built into the Ubuntu unity plugin as of 14.04.

That said, it is rather hard to visualize what is actually seen. So a screenshot or something to clarify what is what would probably help.

---

### Post by mc4man on 2014-09-24
Probably just a small bug (may have seen it once or twice over a long period of time. 
Unity/compiz have a few of these, you could file a bug though no too likely to get much out of it.
> it is rather hard to visualize what is actually seen
It's the highlight (glow color) that surrounds a selected window in the scale spread. Coded into the theme as part of unity deco - ex. in ambiance - 

/usr/share/themes/Ambiance/gtk-3.0/apps/unity.css lines 14,15
 ```
  -UnityDecoration-glow-size: 10px;
    -UnityDecoration-glow-color: rgb (221, 72, 20);

```

It (UnityDecoration-glow) may be enabled in spread via the compiz source (for scale) or maybe in unity, I guess one could ck. in gnome flashback (compiz

---

### Post by matt_symes on 2014-09-24
Hi

> killall -9 compiz

Are you really sure you need to use SIGKILL ?

Do any of the other signals, such as SIGTERM, work to close compiz in a way that is not quite so drastic as SIGKILL ?

Kind regards

---

### Post by bokiscout on 2014-09-24
How it is:
[IMG]http://s24.postimg.org/q7rpnhrpw/Screenshot_from_2014_09_24_21_07_00.jpg[/IMG]

How it should be:
[IMG]http://s24.postimg.org/tg0sea3dg/Screenshot_from_2014_09_24_13_15_12.jpg[/IMG]


My guess is that this is somehow related with dcoonf-editor. After installing that package to change the speed of minimize application the problem occurs, but I can not confirm this without performing new installation.


> **matt_symes said:**
> Are you really sure you need to use SIGKILL ?

Do any of the other signals, such as SIGTERM, work to close compiz in a way that is not quite so drastic as SIGKILL ?

Kind regards
I'm a newbie and I don't fully understand what you are talking about, I know that "killall -9" is forcing the app to quit immediately without following any procedure for "safe" closing, also I know that "killall -15" is much safer approach cause it is forcing the app to quit in more elegant way but I don't fully understand the purpose and deference of two.

What is your suggestion?

In addition killall -15 is closing compiz but it does not start up again, but killall -9 is closing compiz and the compiz is being started up automaticaly and immediately, that's why I use second one.

---

### Post by CantankRus on 2014-09-24
Try using
```
setsid unity
```

The selection glow color can be set using **compizconfig-settings-manager**(ccsm).
Found in the **expo** plugin.
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by bokiscout on 2014-09-25
> **CantankRus said:**
> Try using
```
setsid unity
```

This command have the same effect as "killall -9 compiz". It restores thee glow effect (previously I called it shadow) but after reboot  the glow effect is missing again so I must run this on every boot. If this is safer approach than kill all I will use it. Please confirm this.


Yesterday I created a script that is being run at every boot:
```
#!/bin/bash
# kill/restart compiz to solve glow issue in expo plugin (Super + S)

sleep 3 && killall -9 compiz &
```

to be changed to:
```
#!/bin/bash

sleep 3 && setsid unity
```

I call this a temporary solution, I'm still waiting for permanent solution that will not depend on restarting unity/compiz on every boot.


> **CantankRus said:**
> The selection glow color can be set using **compizconfig-settings-manager**(ccsm).
Found in the **expo** plugin.
Already tried that.

At first I changed color, but no effect. Restart the OS still no glow, than I change back to default color and again no effect, restart the OS no effect. Kill compiz with "killall -9 compiz" whatever glow color is defined in ccsm as you stadetd above is visible.



Edit:
"setsid unity" is messing icons order in left panel, new icons are being placed on top - above all icons locked to left panel, and Alt+F4 shortcut used to close programs is not working.

---

### Post by CantankRus on 2014-09-25
Does the glow work in the guest or a new user account if you enable workspaces?
Could try setting compiz/unity back to default.
```
dconf reset -f /org/compiz/
```

---

### Post by bokiscout on 2014-09-25
> **CantankRus said:**
> Does the glow work in the guest or a new user account if you enable workspaces?
Could try setting compiz/unity back to default.
```
dconf reset -f /org/compiz/
```
The guest user is working fine, but my (the one and only created while installing the OS) still have the issue with glow color even after "dconf reset -f /org/compiz/"


This is very strange.

Meanwhile I did a clean installation with minimal_cd.iso by performing only "sudo apt-get install --no-install-recommends ubuntu desktop". On top of that minimal instalation I added application menu indicator with all of its gtk and qt dependencies, session indicator, application lenses, hud, diodon, firefox, gparted, eclipse, libre office, rhythmbox, htop, copy (online storage) and nvidia proprietary drivers (331.x the ones marked as tested). That's all. No any kind of modifications of compiz or unity settings. Just minimal isntalation and the software stated above.

First few reboot's there wasn't any issues and suddenly the glow color is missing again.

Guest user is not affected this time too, everything is fine there, but my user (the only one existing besides guest) have the issue.

The "kill-all -9 compiz" is doing fine job restoring the glow color, the "setsid unity" is restoring the glow effect but still messing the order of icons in left panel.

---

### Post by mc4man on 2014-09-25
Somehow I got myself sidetracked into thinking you meant the scale/spread glow vs. the expo glow which are 2 separate things altogether.
The expo glow does disappear randomly here also, clearly a bug though don't see one in small search of the 1000+ open ones. 
(- the odds of being fixed for unity7/compiz are nil anyway.

The other option  to returning it would be to change the color in ccsm, will return in next session

---

### Post by bokiscout on 2014-09-26
It is a bug of compiz or some settings are in conflict. However I can not use my system without those modifications so I ended up with above stated script to kill compiz on every boot.

I made a third fresh installation, but this time from standard (not minimal) .iso image. The results are the same. First few boots there is glow color then it is missing.

Thank you all for your suggestions.

---

