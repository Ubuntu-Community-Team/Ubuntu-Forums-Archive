---
title: "Brightness and Lock issue after update?"
date: 2013-03-16
forum: General Help
---

### Post by mickee384 on 2013-03-16
First of all, please excuse me if I am doing this wrong. I have been using ubuntu 12.04 for a while now. A week or so ago, the lock portion of the brightness and lock feature stopped working. I think maybe shortly after the update that week. In any case, I have been looking thru the forums and on the net in general and while I find a fair amount of cases where this is occurring, none of the fixes I have tried so far have rectified the issue. I have done some things, re downloaded the Gnome Screensaver and it works. Just not the lock. I can use CTRL+ALT+L to lock the screen manually, I just prefer to have it lock after the screen goes blank (I am assuming that's the Gnome screensaver), Any advice would be graciously accepted by this newbie. Also if I am violating any forum rule, please let me know. Thanks!

---

### Post by mickee384 on 2013-03-17
Thought I would let you know what I have done thus far:

-used brightness and lock in several ways, every combination, only the blank screen functionality works
-removed gnome-screensaver, rebooted and reinstalled it. 
-ps -e|grep gnome-screen*  shows--> 3081 ?        00:00:01 gnome-screensav
-ran terminal -->gsettings set org.gnome.desktop.screensaver idle-activation-enabled true

Can't find the screensaver in dconf org>gnome
Can't find anything in ccsm
In Ubuntu Tweak, Session Indicator the lock screen is not disabled
All power options are disabled ie: suspend, hibernate etc

Oh, and I am using Unity Ubuntu 12.04

Hope some of this helps!

---

### Post by mickee384 on 2013-03-18
weird. Fixed now. Although I tried so many things, not sure how I did it.

---

### Post by mickee384 on 2013-03-18
I will mark as SOLVED. However, if any one happens to be able to figure out why it suddenly started working yesterday after 2 weeks, please let me know.

---

