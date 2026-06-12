---
title: "MP3 Sound Levelling"
date: 2008-01-17
forum: General Help
---

### Post by markclewis1 on 2008-01-17
Is there an available software package for Ubuntu that will go through my sound files and level the sound volume of the songs so that they are all the same?  Just curious if anyone is aware of an app that will.

Thanks!

---

### Post by jeffus_il on 2008-01-18
Yes, there is software to do it, many players have an option to do it. 
It's called normalizing, Use Synaptic or adept package managers and type normalize in the search box. Then install.

---

### Post by vanadium on 2008-01-18
For mp3 files, the answer is mp3gain. For ogg, there is vorbisgain, but this only works using tags. Thus, it depends on the softwareplayer whether the volume is correctly adjusted. I do not know how widespread support for replaygain tags is, but I am afraid it is not very big (mpd does).

---

### Post by logos34 on 2008-01-18
agree with vanadium.  normalize-audio just does what's called 'peak amplitude' normalization...replaygain uses a perceptually-based algorithm to adjust volume, relative to other tracks.  It also does not alter the songs in any way, just adds playback info to tags.  It's the better wayto go.  You don't even need to run mp3gain manually--Amarok will handle all this using one of the scripts.  Audacious also handles gain playback for all the formats

---

### Post by markclewis1 on 2008-01-18
Thank you for the help!!  I use Amarok for a player.  I will take your advice.

---

### Post by markclewis1 on 2008-01-18
Sorry to keep this thread going, but I am trying to gain a clear understanding of how mp3gain works.  Once installed from synaptic, does it integrate with Amarok so that files played going forward are levelled against each other in a playlist?  Or is there something physically that I will need to do in the Amarok setup in order for mp3gain to function properly?

Thanks again for the help!

---

### Post by Whiffle on 2008-01-18
In amarok, go to Tools > Script Manager.  amarok_replaygain.py might be listed there, if not, you can probably find it with the Get More Scripts button.  Once you have it, Select it, and click Run.  Note that if you don't have all the dependencies installed, it won't run.

---

### Post by markclewis1 on 2008-01-18
Thank you for the information and better understanding on this!  I have followed your instructions and everything is working exactly the way that I was hoping!

Thanks!!

---

