---
title: "No Sound With Upgrade to Gibbon"
date: 2007-10-19
forum: General Help
---

### Post by 5thape on 2007-10-19
I was playing an mp3 as my comp was upgrading to Gutsy Gibbon from Feisty I noticed the sound cut out.  I just thought maybe it'd get fixed once the upgrade was complete and the comp was restarted.  It did all that but I still don't have any sound.  When I go into System -> Preferences -> Sound, if I try to test the sound I get this error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

I'm using a Chaintech AV-710 soundcard.

---

### Post by ijustam on 2007-10-31
This happens to me.  I rebooted once, got the "Login ready" noise and that was it.  No sound since.

---

### Post by Fire_Chief on 2007-10-31
You may want to try using the driver for the Albatron PX865PE. Supposedly, it is nearly the same card and should work with the chaintech av-710.  Just a thought.

---

### Post by ijustam on 2007-10-31
Oh hey I just fixed it.  My .asoundrc file in my home directory was overriding /etc/asound.conf.  My asound.conf file is as it is [here]("http://phoronix.com/forums/showthread.php?t=556").

---

