---
title: "Sound works, then dies"
date: 2005-05-13
forum: General Help
---

### Post by robogock on 2005-05-13
My problem is this: when I first boot up and log in to X, my sound works perfectly. I get the random Gnome noises, I can play mp3s in xmms, I get AIM notification sounds, etc.  Then I leave my computer for a while, and when I come back, sound is no longer working, at all. Another oddity: when xmms tries to play an mp3, not only does no sound come out, but it also appears to be trying to play at hyper speed.

I'm running Hoary on an AMD64 setup. My soundcard is whatever's built in to the motherboard. No sound channels are muted. This has happened to me several times since upgrading to hoary (sound was fine on warty, save a few dvd syncing issues). I've never seen sound die while I was using the computer, only when I've come back after not using it for at least a few hours.

I'm not even sure what information I need to provide for someone to help me, so please let me know what might be useful.

---

### Post by monchichi on 2005-05-14
What output driver are you using in XMMS?

esd, alsa, oss...?

If you're using esd, try replacing it with polypaudio (apt-get install polypaudio). Or just use alsa in xmms and disable the esd server in System>Preferences>Sound.

setting up a .asoundrc file helps get the most out of your sound card also.

---

### Post by robogock on 2005-05-14
I believe it's currently using esd, yes. I'll try changing that, but the thing is, I lose *all* sound on the computer, not just from xmms. I really don't think it's an xmms-setting problem.

---

