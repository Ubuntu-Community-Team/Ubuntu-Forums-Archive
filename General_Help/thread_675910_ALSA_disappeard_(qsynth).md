---
title: "ALSA disappeard (qsynth)"
date: 2008-01-23
forum: General Help
---

### Post by Holonet on 2008-01-23
Ok, so I've been using qsynth/fluidsynth for a while to load an sf2 file and been playing MIDI in Rosegarden.  I recently updated qsynth and fluidsynth to their latest versions (the repositories are behind the lighthouse on this).  So I tried it out after I installed them, everything went fine.  Now I've come back a bit later (computer has been restarted since, if that could possibly matter), and I tried to open qsynth, and it says it failed to create MIDI driver (alsa_seq).  In the audio settings, alsa has gone from the list of choices, I have just oss and file.  Anyone know why this just happened?  I'm getting a few too many problems like this that make it difficult for me to defend this in deference to Windows...:(

P.S.  The sound in general is still fine...can play mp3s...my device in the audio preferences says CA0106 (Alsa mixer)

---

### Post by Holonet on 2008-01-27
Ok I see I'm not the only one who doesn't know what's wrong here.

Anyway, I have since separated my home folder onto a different partition and reinstalled ubuntu (7.10), and freshly installed both fluidsynth and qsynth...and the same problem still exists!  I even tried canning them and installing the old versions via the package manager--no change.

Again, I still have sound for playing mp3s, etc..., and since I just reinstalled ubuntu, it has got to be some configuration or something in the home folder.  I combed through hidden directories looking for program settings but I found jack (no pun intended).  It was working and it just stopped :mad:...little help?...

---

### Post by Holonet on 2008-01-28
Alright pinned down the cause.  It's the "newer" version of qsynth.  I reinstalled Ubuntu, and the problem remained.  I did it again, only this time, I deleted every hidden folder I could from the home folder as well. and that actually gave me a true fresh start.  First orders of business were installing fluidsynth and qsynth, and everything went like it was supposed to.  I upgraded fluidsynth to .8, all's well, I upgraded qsynth to .32 or whatever it is, and the ____ hit the fan.  Specifically, it cannot find the alsa audio driver (not MIDI, audio) after I upgrade qsynth.  So I did sudo apt-get remove qsynth --purge, removed the upgraded executable, every setting I could find, every file that had any suspicious resemblance to qsynth that I could find except the bloody icon file, and then reinstalled the older version of qsynth, started it up, and the problem is STILL there.

I'm kind of at my wit's end with this.  I really would appreciate it if someone could tell me what's going on here.  At least now I know I can fix it, but I shouldn't have to wipe out everything and reinstall just to fix this.  What on earth does qsynth screw with?

---

