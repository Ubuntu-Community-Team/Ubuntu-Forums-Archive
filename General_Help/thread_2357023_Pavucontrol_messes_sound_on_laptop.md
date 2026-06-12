---
title: "Pavucontrol messes sound on laptop"
date: 2017-03-29
forum: General Help
---

### Post by aprekates2 on 2017-03-29
when i choose from pavucontrol earplugs  and from alsamixer i unmute the speaker i get sound from speakerwhen i choose from pavucontrol - speakers  and from alsamixer i unmute the earplus column i get sound from speaker!

So i made a tmp fix with a shell script that load alsamixer settings at startup.

I cant find alternative to pavucontrol.

---

### Post by Bucky Ball on 2017-03-29
Just wondering why you're trying to tweak both. Pulse integrates with ALSA so setting up Pulse then tweaking ALSA is, yes, going to screw things up.

Set ALSA how you want it, leave it, configure Pulse how you want it. On my regular desktop machines I never touch ALSA. I only use PAVControl to control audio and ALSA 'just works', at least for me. :)

Guess the main thing to take away is that Pulse and ALSA do not work independently in Ubuntu. They play together. If you start tweaking ALSA you are going to start changing the options available in Pulse.

---

### Post by howefield on 2017-03-29
Thread moved to the "*General Help*" forum.

---

### Post by aprekates2 on 2017-04-03
The laptop didnt have sound. That's why i started to setting the alsamixer and it worked.

---

