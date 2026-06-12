---
title: "&quot;Just Works&quot; Sound Recording Package?"
date: 2005-06-11
forum: General Help
---

### Post by ksoze on 2005-06-11
I chose ubuntu as a platform due to its "just works" philosophy.  After running it for several days, I am very pleased with ubuntu in general, and appreciative of all the work that has gone into it.  However, my primary intended use for this system is as an audio jukebox and music recording station.  Now mind you, I am not doing pro mixes on this thing, and don't have a MOTU box or other such gear hooked up.  Just a nice sound card.  I just want to be able to record track over track for demo purposes.  Audacity and ardour are both well regarded packages, but neither seems to work with ubuntu out of the box (ardour needs a lot of JACK fiddling and audacity won't play nice with esd), and I'm trying to stick with "it just works" and not get sucked into the old trap of spending more time configuring my system than I spend using it to do useful things.  Sweep is ok, but is really more of a dj tool, and has the unpleasant characteristic of requiring that you set the file time length up front (I can't figure out what that's for).

Can anyone here advise on a good, simple, but reasonably featured audio recording package that "just works" on ubuntu?

---

### Post by gil-galad on 2005-06-11
Audacity.  If you have a good sound card with hardware mixing you do not need to use esd, and probably shouldn't.

---

### Post by ksoze on 2005-06-11
But esd runs by default.  I don't want to have to kill it every time I record (which is what I'mhaving to do now).  I'm hoping something will work with what comes in the ubuntu install.  Hence, the "just works" title.

---

### Post by gil-galad on 2005-06-11
Gnome loads esd by default, but you can easily make it stop by going to
System->Preferences->Sound-> Uncheck "Enable Sound Server startup"

---

### Post by ksoze on 2005-06-14
OK, thanks.  If I do that, will I kill sound in GNOME?  I'd like to use this machine both as a jukebox and a recording station.  I suppose I'll just try it out and find out for myself.  Thanks again.

---

