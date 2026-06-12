---
title: "Lubuntu screen goes completely black after 15 minutes"
date: 2015-01-03
forum: General Help
---

### Post by childintime on 2015-01-03
[SIZE=3]Hello,

[COLOR=#333333][FONT=UbuntuRegular]I just freshly installed Lubuntu 14.04.01 on old laptop and on each fresh reboot after ~15 minutes while doing stuff screen goes completely black with no options on returning to desktop. Notice I am using laptop while this happens (laptop is not idle at all). The audio still plays, but I must reboot otherwise not possible to leave black screen.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I disabled screen saver, and light lock and installed xscreensaver and put
[/FONT][/COLOR][/SIZE]
```
[Desktop Entry]
Name=Screensaver
Type=Applicaton
Exec=xscreensaver -nosplash
```

[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]to /etc/xdg/autostart/screensaver.desktop.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]but still the same. I am not even sure if that's related to screen saver because it seems to be impossible to leave that black screen (and it happens while I am using computer).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any ideas how to fix this?[/FONT][/COLOR][/SIZE]

---

### Post by kerry_s on 2015-01-03
xset s off -dpms noblank

i think thats the command you need to add to startup.

---

### Post by childintime on 2015-01-03
> **kerry_s said:**
> xset s off -dpms noblank

i think thats the command you need to add to startup.

After running this I get: ```
xset: unknown option: noblank
```

I can run ```
xset s noblank
``` though.

---

### Post by Dennis N on 2015-01-03
If your system has not been idle (no mouse or keys used) for at least 10 minutes when this happens, I really doubt it is caused by dpms, which in all reports I have seen kicks in after 10 minutes of inactivity (unless supressed by some other application, such as the xscreensaver daemon). Neither will xscreensaver become active unless the system is idle for the time specified in its settings. Further, a blank screen from either of these restores immediately when you do any keyboard or mouse activity. Sorry - no ideas on what might be your cause, but someone else may know.

---

### Post by grahammechanical on 2015-01-03
Does this happen when the laptop is running on mains power?

---

### Post by childintime on 2015-01-04
> **Dennis N said:**
> If your system has not been idle (no mouse or keys used) for at least 10 minutes when this happens, I really doubt it is caused by dpms, which in all reports I have seen kicks in after 10 minutes of inactivity (unless supressed by some other application, such as the xscreensaver daemon). Neither will xscreensaver become active unless the system is idle for the time specified in its settings. Further, a blank screen from either of these restores immediately when you do any keyboard or mouse activity. Sorry - no ideas on what might be your cause, but someone else may know.

Yep, it's not idle at all, and not possible to leave that, I tried all key combinations.

> **grahammechanical said:**
> Does this happen when the laptop is running on mains power?

Yes running on main power source, not a battery.

---

### Post by childintime on 2015-01-04
Update: The black screen appears immediately but first 5 seconds or so it's not 100% black and I can barely see the desktop background, but after several more seconds it becomes 100% background. As if someone reduced brightness to 95% and then in 5 seconds to 100%.

Also happens almost instantly when opening youtube video in chrome.

---

### Post by kerry_s on 2015-01-04
yeah thats what it looks like just before sleep.

run this in terminal:
xset -dpms

and

xset -q

just copy & post 
dpms (energy star) part so we can see whats on.

like this:
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

---

### Post by childintime on 2015-01-04
> **kerry_s said:**
> yeah thats what it looks like just before sleep.

run this in terminal:
xset -dpms

and

xset -q

just copy & post 
dpms (energy star) part so we can see whats on.

like this:
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

Thank you sir, but I already installed CrunchBang Linux, because I was in a hurry to have operating system. Now CrunchBang does not have this problem, so at least we know it's not hardware problem. Now unless I reinstall Lubuntu once again, I probably won't be able to test your solution.

---

### Post by kerry_s on 2015-01-04
> Thank you sir, but I already installed CrunchBang Linux, because I was in a hurry to have operating system. Now CrunchBang does not have this problem, so at least we know it's not hardware problem. Now unless I reinstall Lubuntu once again, I probably won't be able to test your solution.

#!crunchbang is a good option to. i been playing with elementary os, it just comes with the barebones apps & i just install whatever i want.

---

### Post by childintime on 2015-01-05
> **kerry_s said:**
> #!crunchbang is a good option to. i been playing with elementary os, it just comes with the barebones apps & i just install whatever i want.

I also tried elementary OS, but on my 6 year old 1Gb ram laptop it was running very slow for some reason, even idle ram consumption was much higher. Then tried Lubuntu but it had weird issues, and finally CrunchBang which works well and has best performance with this laptop by far.

---

### Post by amadness on 2015-05-02
In Light Locker, just move the arrow in "Blank screen after" as far to the right as possible.

---

