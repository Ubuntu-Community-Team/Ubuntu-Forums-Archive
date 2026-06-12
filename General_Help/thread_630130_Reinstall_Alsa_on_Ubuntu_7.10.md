---
title: "Reinstall Alsa on Ubuntu 7.10"
date: 2007-12-03
forum: General Help
---

### Post by gdr8205 on 2007-12-03
hey guys i had unistalled Alsa due to thinking it was causeing some sound problems so i installed OSSv4,  which workd for about 2 days so i was wondering how do i reinstall alsa?

---

### Post by doooh_head on 2008-01-29
Does anybody have an answer to this?  I too uninstalled ALSA in an attempt to "fix" some sound related problems by installing and setting up OSS but now everything is worse.

I would prefer to just reinstall ALSA but I am currently comtemplating reinstalling Ubuntu otherwise.

Anybody?

---

### Post by Agent ME on 2008-01-29
I found these scripts somewhere online, I can't remember where, and they don't have any author info in them, so I don't take credit for these - and I couldn't remember where I found them, so I just uploaded them onto an account I have.

Run the first one, and when its done, reboot, and then run the second one... and I guess reboot again, and you'll be upgraded to alsa 1.0.15.

[http://am49.frih.net/misc/alsa_1.sh](http://am49.frih.net/misc/alsa_1.sh)
[http://am49.frih.net/misc/alsa_2.sh](http://am49.frih.net/misc/alsa_2.sh)

Oh, run them as root with sudo too.

---

### Post by mwacky on 2008-01-30
Thanks!  I ran into the same issue, my sound was fine then all of a sudden it was not working.  i took a look at the scripts and figured it was worth a shot.  Ran rebooted, ran rebooted.  Now I still have no sound and get an error about the gstreamer plugin, I looked into my packages to see it was installed, and version 0.10, perhaps it is out-of-sync with the newer alsa driver?

---

### Post by Agent ME on 2008-01-30
The latest gstreamer packages in the package manager work for me with the latest ALSA. Do you have gstreamer0.10-alsa? Just a random guess I'm throwing out.

---

### Post by mwacky on 2008-01-30
Thanks for the suggestion, I had these packages and reinstalled all gstreamer packages with synaptic.  My guess is the sound card driver is no longer working, I get the attached error message, not sure where to look to fix it.

---

### Post by mwacky on 2008-01-31
Fixed all my issues!

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

This article is great!  It is long and a little complicating, I ended having to use the drivers from the alsa project, but it fixed me, This is the best place to start if you are having sound issues.

---

