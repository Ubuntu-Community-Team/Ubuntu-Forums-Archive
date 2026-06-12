---
title: "Can't get audio while playing music"
date: 2008-05-03
forum: General Help
---

### Post by Predtech on 2008-05-03
Hi guys. I ahve a bit of a strange problem. I am running the new 8.04 version of Ubuntu that i love to death. The one strange thing i noticed is that when i play music through Amarok or Rythmbox i can't get any audio from any other aplication, like web based flash vids, or even messages from Skype.

Can anyone tell me why this is happening?

thanks

---

### Post by garbit on 2008-05-03
im having the same problem its really strange?

---

### Post by Cresho on 2008-05-03
you need to tell us your hardware specs.  I have no issues when I am playing amarok, playing typhoon 20001, watching a dvd video, a high definition television, regular analog television, dvd movie all running at the same time under my audigy 2 24bit audio system.  in your audio, try using the alsa accross all.

---

### Post by argosreality on 2008-05-03
That's because of the new audio layer called PulseAudio. Neither Skype nor Flash work out of the box. For flash you just need to download a plugin for PulseAudio in the repositories. Not actually booted into my ubuntu drive at the moment due to the numerous issues I've had with Hardy so I can't give you the exact plugin but a search for pulse in Synaptic will show the libflashpulse (I think?) you will need for flash to work

---

