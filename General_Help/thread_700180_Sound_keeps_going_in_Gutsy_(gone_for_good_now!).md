---
title: "Sound keeps going in Gutsy (gone for good now!)"
date: 2008-02-18
forum: General Help
---

### Post by m15hun on 2008-02-18
Hi Folks,

I have been using Ubuntu for a while now but have recently had a problem with my sound disappearing (for want of a better phrase). I am using C-Media CMI9880.

I was booting up, using the OS for a while and it would be fine then I would try to listen to an .mp3 or watching a film and it would be silent. Everything is on and working (speakers etc.) but no sound can be heard. I **was** rebooting and it was fine, now it isn't - it just boots back up silently.

I've been into sound settings and tried OSS and ALSA, i've tried leaving it on autodetect and taken it off and put it onto 'open sound system'. Whenever I click test I get:

*Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'*

Could anyone offer any advice?

---

### Post by m15hun on 2008-02-18
Just an update to this:

My sound is perfectly fine in Windows (I dual boot). Is the only answer to re-install Ubuntu (again!?), I really don't want to have to move back to Windows but this will be the 7th time I've had to reinstall Ubuntu..:(

---

### Post by m15hun on 2008-02-19
Any chance of some insight into this?

Thanks.

---

### Post by pointone on 2008-02-19
You can try reconfiguring ALSA with "sudo alsaconf". Otherwise, I'm at a loss.

---

