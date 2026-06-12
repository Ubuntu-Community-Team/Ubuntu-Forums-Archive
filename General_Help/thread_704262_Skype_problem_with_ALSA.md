---
title: "Skype problem with ALSA"
date: 2008-02-22
forum: General Help
---

### Post by atom32k on 2008-02-22
Hello

I have problem running skype after installing latest ALSA drivers on my Kubuntu Gutsy (Toshiba A200 Intel sound).

When i try to run Skype then it hangs on signing in (probably cannot play signing in sound). After that i cant kill skype process even as a root or restart alsa driver also ProcessTable show nothing as it hangs too.

So after that i cant even reboot only turn off and turn on lappy again.

When i /etc/init.d/alsasound stop before launching skype it works ok but of course without sound in system. :(

---

### Post by epsilorn on 2008-02-28
Hi, I've got the same laptop and the same problem!! If skype doesn't start everything else works. If I try to start skyoe then even wine stops working! :(
Also if this happens then I cannot shut down my computer, it hangs shutting down KDM forever.

---

### Post by Michl on 2008-02-29
error

---

### Post by Michl on 2008-02-29
I'm having similar problems with skype on a desktop running gutsy.  It worked,
but after one of the latest updates it doesn't even load.  Also, you cannot
just end process in system monitor, but have to right click and choose
kill process.  Shutdown is also slow until I kill and remove skype.  Funny
thing is Skype is also not working correctly on my laptop where it
used to work.  There it has problems with audio playback, which
was not an issue under Hardy before.  Something has changed
in skype.

---

### Post by epsilorn on 2008-03-04
no ti's not a problem with skype, but with alsa 1.0.16, also wine stopped working for me and also k display manager. Downgrading to ALSA 1.0.15 everything started working again but my soundcard behaves bad with this driver.

---

