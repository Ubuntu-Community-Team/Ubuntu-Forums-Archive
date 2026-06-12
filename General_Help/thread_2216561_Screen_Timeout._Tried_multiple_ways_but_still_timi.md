---
title: "Screen Timeout. Tried multiple ways but still timing out"
date: 2014-04-12
forum: General Help
---

### Post by BB91103 on 2014-04-12
Hello Forum,

A very inexperience user here. What I did was installed Ubuntu 12.04 LTS on my 4 years old Gateway laptop after the hard drive crashed. I am only using it to watch TV and surf the web.

It has been 2 months and at first everything was working fine. Then about 2-3 weeks ago I was watching a movie and the screen went blank. When I touch the touchpad the screen would come back on. So I tried several things but nothing seem to work.

_**Attempt 1**_
System Settings
Brightness
Uncheck Dim screen to save power
Selected "Never" for Turn Screen off when inactive
Selected "Off" for Lock

**_Attempt 2_**
System Setting
Power
Selected "don't suspend" and "Do nothing" for pretty every scenario

_**Attempt 3**_
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false

I have ZERO experience with Linux. Your help is appreciated.

---

### Post by germanix on 2014-04-12
So far you have done everything right. What you have done should have solved your problem. What you can try now is go to your applications, then find the application "startup-applications". There you will find the "screensaver". Make sure you un-tick the box of "screensaver". The change may only take effect after a re-start.  Ubuntu no longer has a screen saver (since 12.10) but the Gnome screen saver is still there. If that box is already un-ticked see if there are any other screensavers active under start-up applications and uncheck those. Other than this I have no ideas. my settings are like yours and I do not have this problem. Hope you get this solved.

---

