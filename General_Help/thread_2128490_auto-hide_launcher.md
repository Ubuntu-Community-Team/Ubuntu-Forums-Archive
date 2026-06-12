---
title: "auto-hide launcher"
date: 2013-03-23
forum: General Help
---

### Post by TerryWJ on 2013-03-23
I need help. I am using Ubuntu 12.04.2. I want to set the launcher to auto-hide. Nothing works. I have tried using CCSM, Ubuntu Tweak, Tweak Tool, Unsettings, and MyUnity. On these apps, as soon as I click auto-hide, within a second it automatically goes back to always show launcher. I need help. I even tried Google to see if I can find a solution. HELP????????

---

### Post by GreatDanton on 2013-03-23
Copy paste this in terminal, restart computer, and try again.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

As far as I know you don't need aditional programs for auto hiding launcher. Auto hide launcher option should be in system settings/appearance

---

### Post by TerryWJ on 2013-03-23
I have done that twice now. Nothing.

---

### Post by mc4man on 2013-03-23
> **TerryWJ said:**
> I need help. I am using Ubuntu 12.04.2. I want to set the launcher to auto-hide. Nothing works. I have tried using CCSM, [COLOR="#0000CD"]Ubuntu Tweak, Tweak Tool, Unsettings, and MyUnity[/COLOR]. On these apps, as soon as I click auto-hide, within a second it automatically goes back to always show launcher. I need help. I even tried Google to see if I can find a solution. HELP????????
Do you have all those apps installed ?

I'd try completlely removing all the blue ones, then restarting.
After restart, right click on Desktop > Change Desktop Background > Behavior, set auto-hide there & see what happens

---

### Post by TerryWJ on 2013-03-23
I just now did what you suggested. As soon as I clicked the ON button, it shifted back to OFF.

---

### Post by mc4man on 2013-03-23
A bit of a mystery - 
If you were to login to a guest session can you change the launcher to autohide? (thru the right click on Desktop , ect.

Assuming you are using unity, not unity-2d, you could check with 
```
env | grep -i "^desktop_session" && env | grep -i "xdg_current_desktop" && env | grep -i "compiz"
```
should return 3 like
DESKTOP_SESSION=ubuntu
XDG_CURRENT_DESKTOP=Unity
COMPIZ_CONFIG_PROFILE=ubuntu

So if in a ubuntu session (unity) can you write to this file?,
```
 gedit ~/.gconf/apps/compiz-1/plugins/unityshell/screen0/options/%gconf.xml
```
 if so look for this line & change red to 1 (blue will be different, doesn't matter
> <entry name="launcher_hide_mode" mtime="[COLOR="#0000CD"]1364055559[/COLOR]" type="int" value="[COLOR="#FF0000"]0[/COLOR]"/>
Then save & log out/in

Additionally - 
if you open ccsm from a terminal what profile does it show being used, should say - 
Profile     : unity

Worst case you could also try resetting unity - 
```
unity --reset &
```

---

