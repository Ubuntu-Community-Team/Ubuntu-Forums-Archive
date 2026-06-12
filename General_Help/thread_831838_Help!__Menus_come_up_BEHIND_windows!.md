---
title: "Help!  Menus come up BEHIND windows!"
date: 2008-06-17
forum: General Help
---

### Post by Metallinut on 2008-06-17
I've been searching the forums, but have been able to find a post similar to my problem.  So I apologize if this has been handled before.

I just recently started getting into GTK themes from gnome-look.org.  I set a theme (I believe this is the only change to my machine that has triggered this new behavior), and now all my menus, drop boxes, tool-tip popups, etc. come up BEHIND the window I'm working on.  In the screenshot, that's uTorrent running in Wine, but this happens on all programs.

It's probably just a setting somewhere, but I've been unable to find it, and it's REALLY annoying!  HALP!  :mad:

---

### Post by Kevbert on 2008-06-17
It might be System-Preferences-Windows 'Select Windows when mouse moves over them'.

---

### Post by Metallinut on 2008-06-17
> **Kevbert said:**
> It might be System-Preferences-Windows 'Select Windows when mouse moves over them'.

Unfortunately no.  That was unselected.  Selecting it did not change my pop-up/right-click/etc. behavior.

---

### Post by Metallinut on 2008-06-17
Weird.  I started messing with some screenlet settings...I had installed the MLB standings and MLB player screenlets, and turned off "Keep Above".  When I stopped both of these screenlets, menus started appearing above the window again.

I reset the two screenlets, and turned them back on.  I even turned off "Keep Above" on them again, and the menus are still working properly.

I'll keep an eye on it, but things seem better now.  Strange...

---

### Post by Kevbert on 2008-06-17
Some screenlets seem to behave oddly.  I'm running the latest Network Wireless screenlet to check amount of data downloaded/uploaded over a month (as capped broadband is common in the UK).  Download seems fine, but uploads are going crazy (even with no connections!!!)  Yet other people seem to have no problems.  Another thing I've noticed is that the screenlets are being displayed randomly on different workspaces, but always in the correct position and all on one workspace.

---

### Post by Tomatz on 2008-06-17
It may be a setting in compiz causing the problem. In a terminal type:

```
metacity --replace
```

This will disable compiz so you will be able to see if it is a setting in compiz causing the problem.

If it is compiz, post back so i or someone else can hunt down the setting ;)

---

### Post by Kevbert on 2008-06-18
Hi Tomatz.  I assume that you suggested I turned off compiz and not Metallinut.  Turning off compiz doesn't seem to make any difference to my screenlets problems.  I reset the data counter and then looked at a short online video. Download was approx 1.5Mb and upload was 230Mb.  I've posted on the Gnome-look website and I've had no luck with the suggestions.

---

### Post by Tomatz on 2008-06-18
> **Kevbert said:**
> Hi Tomatz.  I assume that you suggested I turned off compiz and not Metallinut.  Turning off compiz doesn't seem to make any difference to my screenlets problems.  I reset the data counter and then looked at a short online video. Download was approx 1.5Mb and upload was 230Mb.  I've posted on the Gnome-look website and I've had no luck with the suggestions.

I was replying to the poster but it was worth a try ;)


It sounds like something is wrong with your screenlets install (probably to do with python)

Go here and download the latest version:

[http://www.screenlets.org/index.php/Download](http://www.screenlets.org/index.php/Download)

There is an unstable repo you can add or a stable .deb to install. I suggest you **completely remove** you current screenlets package via synaptic first.

:)

---

### Post by Metallinut on 2008-07-01
Small follow-up.

I had the problem come back after a reboot (doesn't seem to happen every reboot)...

running:
```
metacity --replace
```
then:
```
compiz --replace
```
does seem to fix it. 

Screenlets manager says it's 0.1.2

---

### Post by Tomatz on 2008-07-01
> **Metallinut said:**
> Small follow-up.

I had the problem come back after a reboot (doesn't seem to happen every reboot)...

running:
```
metacity --replace
```
then:
```
compiz --replace
```
does seem to fix it. 

Screenlets manager says it's 0.1.2

You can use this to reload compiz with a single click.

[http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/)

Install it then add the command **fusion-icon** to your *System, preferences, Session, Startup list*.

;)

---

### Post by Metallinut on 2008-07-01
> **Tomatz said:**
> You can use this to reload compiz with a single click.

[http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/)

Install it then add the command **fusion-icon** to your *System, preferences, Session, Startup list*.

;)

Ah nice!  I suppose I could even have a little bash script that did the two commands, and put that in sessions.

Thanks!

---

### Post by Tomatz on 2008-07-01
> **Metallinut said:**
> Ah nice!  I suppose I could even have a little bash script that did the two commands, and put that in sessions.

Thanks!

Aye you could have but the gui fusion-icon tray app is real handy if you want to easily turn compiz off and back on. If you have emerald installed you can even switch between window decorators ;)

---

