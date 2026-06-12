---
title: "Panel disappears, no Session manager, etc.--what happened?"
date: 2008-06-05
forum: General Help
---

### Post by Mander on 2008-06-05
I am a complete novice with this stuff, so I hope I give enough info.

I'm not entirely sure what happened--I applied all the updates that were available last night, and was messing around with the Compiz settings at the same time.  Suddenly, all kinds of things are going wrong.  

I can't click on any of the toolbars or buttons in Firefox, or it shuts down.  My history and bookmarks aren't there, anyway.  If I type anything at all into Dillo, it shuts down.  If I click on the "restart" button in the panel, all the panels disappear.  All the windows open underneath the top panel, so that I have to use alt+mouse to drag them down where they belong. A pdf file that I was reading two days ago keeps opening up at random.  When I try to open the session manager (system--preferences--session), a message appears in the taskbar but it doesn't actually open. 

I've tried reinstalling compiz, gnome, etc. and anything else I could think of.  If I try to start the gnome settings daemon in terminal, I get this:

** (gnome-settings-daemon:8066): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:8066): WARNING **: Could not acquire name

I also had an error telling me "could not get system bus".

I'm running Hardy, with the latest updates.  It's installed using Wubi, if that makes any difference, and everything was fine until late last night when I applied the updates.

Where do I start with working out what the problem is?

---

### Post by buntunub on 2008-06-30
Wish I could help, but I have the same thing happening here! :(

---

### Post by Motorhead Kaze on 2008-06-30
Same problem here.  For some, THIS [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html) worked, for others, going into HOME, selecting SHOW HIDDEN FILES then deleting files named, ".g" something (like .gnome2, etc.) worked.  But these did not make Gnome work for me.

I also tried accessing ubuntu from a previous kernel (I'm on Hardy) but with no luck. Gnome is just STUCK. Icons and panel cannot be accessed. So, I reinstalled a fresh Hardy.  It worked, but upon installing the 200 or so updates and restarting the computer, Gnome was AGAIN broken!!!

The only way for me to get into Ubuntu is through failsafe mode. 

Honestly, Ubuntu is my daily WORK computer, so time is really an issue. So, until a solution is found, I am going to try a fresh install of GUTSY to see what happens.  A usable Gutsy would be better than using Hardy in failsafe everyday, or so I think.

---

