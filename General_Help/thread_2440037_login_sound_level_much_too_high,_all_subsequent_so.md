---
title: "login sound level much too high, all subsequent sound levels good"
date: 2020-04-05
forum: General Help
---

### Post by RogerDavis on 2020-04-05
At startup, the startup sound is  >MUCH<, >MUCH<, >MUCH< too loud.  Once started and logged in, sound level is good.

This began after a recent update.

How do I adjust the startup sound level to not damage my speakers or house windows ???

Ubuntu 18.04

---

### Post by owbizi on 2020-04-06
It might be because your system reverted your sound settings or is adjusting your audio volume to match the previously set percentage only after the login sound is played.

In that case, you might try and [mute or change the volume at which the login sound plays]("http://ubuntuhandbook.org/index.php/2019/03/disable-mute-terminal-alert-sound-ubuntu-18-04/"). I wouldn't know for sure why that is only happening after a recent update, though.

If that doesn't work, you might also want to try running [pulseaudio in system mode]("https://rudd-o.com/linux-and-free-software/how-to-make-pulseaudio-run-once-at-boot-for-all-your-users") instead of user mode, just to be sure, but be warned of the [disadvantages]("https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/SystemWide/").

---

