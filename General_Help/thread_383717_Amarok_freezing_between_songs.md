---
title: "Amarok freezing between songs"
date: 2007-03-13
forum: General Help
---

### Post by napsilan on 2007-03-13
Is there a way to stop amarok from taking almost all of my cpu while it's switching songs?  This is most noticable if I'm running another program that needs resources (Warcraft 3 for example), and also if I'm skipping songs quickly.  I am using Amarok 1.4.5, xine engine, arts output plugin and kde 3.5.5.  

If I use a gstreamer player (songbird, banshee, xmms, etc) there is no freezing issue between songs but the sound quality seems to be very bad.  

If it matters, I'm also using onboard sound, athlon 64 3200, 2gb ram.  2.6.20.1 kernel, resierfs on /, ext3 on /home.

---

### Post by Lucas2005 on 2007-03-14
Hello there,

I had a similar problem with amarok, that started when i selected to use Crossfading under "Configure Amarok -- Playback"   I guess my current sound card does not support it... i just turned it off and there was no more crashing between songs.

Hope that helps.

---

### Post by napsilan on 2007-03-27
after playing with "nice"ing in ksysguard, artsd seems to be the process responsible. Nicing it to about 3 or 4 fixed much of the problem.

Edit:

I think the poor sound quality in gstreamer (and xine w/o arts) was caused by having the amarok volume at 100%, turning it down and turning my speaker volume up fixed it.

---

