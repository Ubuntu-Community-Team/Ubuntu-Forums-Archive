---
title: "XMMS Equalizer Problems"
date: 2005-09-14
forum: General Help
---

### Post by Tylo on 2005-09-14
I cannot get the Equalizer to function in XMMS. I can move the slides, but none of it has any bearing on the sound output. Does anyone know a fix?

---

### Post by Tylo on 2005-09-14
I suppose it is worthy of note that it is ogg vorbis files that I am trying to play. I just read that the ogg vorbis format cannot be equalized. Is this true?

---

### Post by Tylo on 2005-09-14
Does anyone have any information about this?

---

### Post by arnieboy on 2005-09-14
[QUOTE=Tylo]Does anyone have any information about this?[/QUOTE]
My guess is that u did not turn the equalizer on. check on the main window. therez a small button at the bottom right corner. u gotta turn it on to get the equalizer working

---

### Post by skoal on 2005-09-14
If someone tells you .ogg cannot be equalized, real translation - we haven't implemented that yet.  Shoot, I can poke a hole through a styrofoam cup and squeeze it at the midpoint or use a rag to muffle and distort the sound I make, emulating an equalizer.  It's just a filter.  Try that same .ogg file on Winamp and Windows...

I had a similiar problem like that a year ago using just mp3's.  I filed a bug report with XMMS and they said it was because that format was not supported with the EQ.  I said, "hey, this is just an .mp3 here, and the EQ sliders have always worked reliably in past revisions."  I never heard back from them again...

Anyways, my sol'n (other than using bmp and now amarok) was just to remove the ~/.xmms path, drop my presets in there and try again.  I believe I may have played with the Sound plugin as well (alsa, oss, etc).  It worked.  I don't know why the sliders worked now and they didn't before.  Now, that was for my bug.  Yours may be different.  I think I actually might have rolled back my version 1 or 2 since the eq apparently underwent some changes (I didn't like) as well...

\\//_

---

### Post by Tylo on 2005-09-15
Maybe I'll just get AmaroK. But yeah, the equalizer was on. The newer version's on button is in the top left, I suppose (since you said it was in the bottom right).

---

### Post by ricardisimo on 2007-07-28
I'm having the same problem: the preamp doesn't do anything, and the EQ's sliders make no difference at all. Mind you, they were working perfectly a week ago before I reinstalled (long story, but basically getting rid of problems I inherited from pre-release Feisty). So far as I can tell, everything is ALSA all the way around, so there shouldn't be communication problems. Any ideas?

P.S, - Yes, the EQ is on, and I've even tried everything with it off as well.

---

