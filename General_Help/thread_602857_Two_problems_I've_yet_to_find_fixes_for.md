---
title: "Two problems I've yet to find fixes for"
date: 2007-11-04
forum: General Help
---

### Post by 9Digits on 2007-11-04
I've got two problems I'm hoping someone can offer fixes for.  They've got to be out there, but I've had no luck thus far.

1.  I normally have gnome-panel set to auto-hide, set to 48 in height with 0-1 pixels showing at the bottom of the screen.  I can go into gconf-editor as root in X and do it while logged in that way, but not in my profile.  I know, I shouldn't be logging in as root, but I needed to tell if it'd work there, and it does.  Where do I configure the gnome-panel settings for a non-root user, if I don't want a 6 pixels showing on autohide?

2.  Compiz's menu fade animations (or overall menu response time) is driving me nuts.  It's way too slow, it seems like the fade process is about 2 seconds.  Where can I turn that off or at least speed it up?  I'm at the point where I'm ready to pull the plug on Compiz, just so I can get some work done.

Any help is appreciated.

Thanks!

---

### Post by mikeize on 2007-11-04
As for #2, have you tried the following?

system>preferences>advanced desktop effects settings>animations>close animation

>then look for the entry governing menus (the second entry in mine), and edit the duration field.  You can do the same for the open animation too.  Set it to 0 if you like, and it should be nice and fast!

-mike

---

### Post by 9Digits on 2007-11-04
Thanks for replying.  I've tried in there, but am limited to 50 as the lowest value.  And even if I turn off animations, I'm still getting slow response.  I just want to click on the main menu icon on the panel and have it come up.  Right now it's a situation of clicking, and waiting.

---

### Post by johnn1949 on 2007-11-05
Maybe I don't understand panel question,but could it be as simple as right clicking on panel and choosing properties to change your settings?

---

### Post by 9Digits on 2007-11-05
It's possible to toggle autohide and define the panel size, but it isn't possible to adjust the autohide speed or the pixel overlap (default 6px).  When logged in as root it can be done by going into gconf-editor and editing the panel properties, but it doesn't appear to be the case for other users.

---

### Post by mdurham on 2007-11-05
> **9Digits said:**
> It's possible to toggle autohide and define the panel size, but it isn't possible to adjust the autohide speed or the pixel overlap (default 6px).  When logged in as root it can be done by going into gconf-editor and editing the panel properties, but it doesn't appear to be the case for other users.

I don't understand, maybe I'm missing something. I can set these things with the Configuration Editor as a normal user. There is a hide delay setting in apps->panel->toplevels->(bottom or top)
Sorry if I'm telling you something that you already know.
Cheers, Mike

---

### Post by 9Digits on 2007-11-05
I've already got those set, but it only seems to have an effect to the panels when logged in as root.  

I appreciate you trying to hash it out with me!  I don't think this is a hardware issue as I've got decent hardware.

---

### Post by javaguru on 2008-02-11
> **9Digits said:**
> 
2.  Compiz's menu fade animations (or overall menu response time) is driving me nuts.  It's way too slow, it seems like the fade process is about 2 seconds.  Where can I turn that off or at least speed it up?  I'm at the point where I'm ready to pull the plug on Compiz, just so I can get some work done.


Did you find any solution ? I started using KDE in the mean time ..

---

### Post by StewieGriffin on 2008-05-11
Install compiz-settings-manager.  Run ccsm or use the system preferences.

Go to category effects, animations, effects settings tab.

Increase normal animation speed from 10 to 30 or more.

I think that is what you want.  Slow menu effects drive me crazy.

---

