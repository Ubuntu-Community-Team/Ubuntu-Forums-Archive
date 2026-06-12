---
title: "Full screen using RealPlayer 10 on mlb.tv?"
date: 2005-08-19
forum: General Help
---

### Post by JackWhite05 on 2005-08-19
So I have Ubuntu and RealPlayer 10 installed. I'm using my TV as the sole monitor (although that should have no effect on this problem). I want to watch my baseball subscription package (mlb.tv) through Ubuntu on my TV. It works fine with RealPlayer embedded in a Firefox window. Unfortunately I cannot figure out how to full screen the broadcasts.

Anyone have any idea of what I need to do, or even if it is possible?

Thanks

---

### Post by russbuss on 2006-07-01
I have performed the following steps and now get mlb.tv in an un-embedded window.  However, if you went to full screen the resolution would be pretty low.

To quote prof_booty:

> First, make a back up of your mplayerplug-in.conf that you can use if this breaks anything.

$ sudo cp /etc/mplayerplug-in.conf /etc/mplayerplug-in.conf.bak

then, edit the file to force mplayer to open the video in a new window

$ sudo gedit /etc/mplayerplug-in.conf

find this line:

#noembed=0

change it to

noembed=1

Then go to mlb.tv and log in before clicking on the streams, this seems to be a key step.

Make sure you notice that you have to remove the "#" before "noembed". I failed to notice this and it didn't work for me at first.

Hope this helps.

---

