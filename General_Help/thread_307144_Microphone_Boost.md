---
title: "Microphone Boost?"
date: 2006-11-26
forum: General Help
---

### Post by olieviya on 2006-11-26
How can I boost my microphone's sound?
I have looked all around the Volume Control. I have tried changing from ALSA to OSS, I cannot find the mic boost. I think it's just not there on my pc, is that possible? I can see the bars to change the microphone's volume and they are on full blast but there is so sign of a boost option...](*,) 

Any ideas?
Thanks

---

### Post by loell on 2006-11-26
have you tried 

gnome-alsamixer , install it if you haven't,

theres mic boost check box in there.

---

### Post by olieviya on 2006-11-26
> **loell said:**
> have you tried 

gnome-alsamixer , install it if you haven't,

theres mic boost check box in there.

Seems like I don't... installing now then...

Hmmm, where exactly is it? I check the drop down menu... nothing... ???

[[IMG]http://img292.imageshack.us/img292/6848/screenshotgnomealsamixeih6.th.png[/IMG]](http://img292.imageshack.us/my.php?image=screenshotgnomealsamixeih6.png)

---

### Post by loell on 2006-11-26
seems like it depends on the soundcard? there's a mic boost checkbox on my gnome alsamixer.

have you check all the check box on menu File-->properties

---

### Post by olieviya on 2006-11-26
> **loell said:**
> seems like it depends on the soundcard? there's a mic boost checkbox on my gnome alsamixer.

have you check all the check box on menu File-->properties

yeah, could it be that the mic shown there is not the one i'm using, since my laptop has a mic input socket but i'm using the in-built one?

input 1-3 all say mic......


[[IMG]http://img84.imageshack.us/img84/914/screenshotoliviaolivialtv0.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshotoliviaolivialtv0.png)


And when a try to tick the checkbox for the other inputs in ALSAmixer I get:
[B][COLOR="DimGray"]
** (gnome-alsamixer:5614): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:5614): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:5614): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

*[/COLOR][/B]

---

### Post by olieviya on 2006-12-04
anybody? :(

---

### Post by Laryllan on 2006-12-07
Take a look at the ALSA page, maybe there is a newer version that supports your sound cards microphone boost.

[www.alsa-project.org](www.alsa-project.org)

They have a soundcard list, see if yours listed there and what features are supported. Maybe subribe to the mailing list to get more information.

It's not easy to get the lastest ALSA sources compiled and running, so check out if it improves anything!

---

### Post by olieviya on 2006-12-07
> **Laryllan said:**
> Take a look at the ALSA page, maybe there is a newer version that supports your sound cards microphone boost.

[www.alsa-project.org](www.alsa-project.org)

They have a soundcard list, see if yours listed there and what features are supported. Maybe subribe to the mailing list to get more information.

It's not easy to get the lastest ALSA sources compiled and running, so check out if it improves anything!

cheers - will do

---

### Post by olieviya on 2007-03-06
I can't seem to find any relevant info about my mic. Still doesn't work on ubuntu - works perfectly under windows.

---

### Post by bgryderclock on 2007-05-23
try this :)
> 
from amklinux -  January 31st, 2007, 11:15 AM

- Go to Applications > Sound & Video > Volume Control (or type gnome-volume-control in a terminal).
- Select Edit > Preferences.
- Check "Mic Boost (+20dB)" and "Capture".
- Select the "Keys" tab and check "Mic boost".
- Play with the sliders in the "Capture" tab. 

This worked with my old vocal mic and my standard thinkpad T30 laptop soundcard.

---

### Post by olieviya on 2007-05-29
> **bgryderclock said:**
> try this :)


This worked with my old vocal mic and my standard thinkpad T30 laptop soundcard.

Mine doesn't have the micboost +20dB thing.

---

### Post by thehuman on 2007-05-29
I'll give you the "audio-guy" answer, and say that you need a hardware preamp. All microphones have very low signals and need circuitry (pref. tubes) to drive them. Boosting it in software is going to add alot of noise and distortion, so if you're going for quality, that may not be such a great option. On the other hand, if you just need to record dictation for note taking or something like that, you could just boost the signal in audacity or a similar wave editor after the fact. It will sound like hell, but if quality is not a issue, who cares?

[This]("http://www.music123.com/ART-Tube-MP-Mic-Preamp-i37170.music") is the preamp I use in my recordings, and I am a snob. It's cheap and it's tube-driven. You will get more mic gain out of this bad boy then you will know what to do with.

---

