---
title: "Generic sluggish PC query"
date: 2006-09-13
forum: General Help
---

### Post by Slychilde on 2006-09-13
I know this gets asked quite a bit, but it's a toughy to search for, and I've already tried some suggestions.  Ubuntu is running a bit slower than I think it should be running.  It took over 10 seconds for Amarok to start up, Opera over 5, etc.  Once they get cached they seem to take less, but still way longer than it should.

My system is:
Mobile Barton @ 2.3Ghz
2 Gigs of OCZ Gold @ 420mhz
Abit NF7-S
40 Gig Maxtor HD 7200 rpm (I think)
-1.3gig swap
-15 gigs for windows NTFS
-rest is for ubuntu
120 gig Seagate 8mb cache 7200 rpm
-35 gigs /home
-rest NTFS Storage
Leadtek Geforce 6600GT

My used ram sits at about 150-300 megs; cpu rarely goes above half unless playing warcraft III or the likes.  Prelinking resulted in no notice-able speedup, and possibly some slowdown. ><  I followed the guide for prelinking written by one of the forum admins.  I'm using the 2.6.15.26-k7 kernel from synaptic.  What else can I do?

Also, what is the equivalent of msconfig in ubuntu, if there is one?

---

### Post by orb9220 on 2006-09-13
Well you may be right for those are about my times 15sec for amarok and 8-10 secs for firefox. My specs is p4 1.3ghz. 640mb ram.

Slow down area's that I have read is no.1 seems to be video drivers not installed or configed properlly (xorg)

2nd seems to be 64bit kernel running 32bit apps. 

3rd trying to run xgl/compwiz  on paticular cobinations of video cards and mobo's with nvidia mobo's and ati video cards being the most problematic.

---

### Post by Bagnaj97 on 2006-09-13
Amarok takes a while to load under gnome because it has to load the all KDE libraries. It should load faster if you're using KDE though.

---

### Post by Slychilde on 2006-09-13
Thanks for the replies, you two. :)

I know Amarok has to load the KDE libs, but I would hope it wouldn't take that long.  I can't complain, though;  it's worth it.  I usually just leave it open on my second desktop, anyways.

> Slow down area's that I have read is no.1 seems to be video drivers not installed or configed properlly (xorg)

2nd seems to be 64bit kernel running 32bit apps. 

3rd trying to run xgl/compwiz on paticular cobinations of video cards and mobo's with nvidia mobo's and ati video cards being the most problematic.

I used Automatix to set my nvidia driver up and I ran the xorg reconfigure aftewards to make sure I am using the Nvidia driver.  Could that possibly affect it?  Oh, and a few weeks later I downloaded the K7 kernel, although dkpg-reconfigure xorg says I' using 'nvidia' driver; anything else I need to do, reinstall, recompile?  Also, I did have XGL/Compiz on here, but I uninstalled them, deleted custom commands from startup script, etc.  It was even slower with it on, and the candy just wasn't worth it.

Does how many packages you have installed also affect run-times, and what-not?  This is my first Ubuntu install (last linux attempt was over 2 years ago), so I have been testing things out as I see them - I have beep, XMMS, listen, and amarok for audio players installed.  Would it help to uninstall the ones I don't use?  I'm not entirely sure how to uninstall them completely outside of going into Synaptic and checking "remove completely."

How about *gulp* compiling a newer kernel, or even recompiling my current kernel?  I have read multiple threads on them, but honestly, they scare the daylights out of me.  Hmm, I guess I have not seen a thread on RE-compiling a kernel, just compiling a new one.

---

