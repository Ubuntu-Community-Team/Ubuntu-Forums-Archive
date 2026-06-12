---
title: "Turn off mute on startup"
date: 2024-04-26
forum: General Help
---

### Post by zorro10678 on 2024-04-26
My aunt has Ubuntu on her computer. I'm not sure which version at the moment. She is blind and has the assistance turned on, but on occasion other people have used her computer. Invariably, when someone uses her computer, they mute it. They could just turn off the speaker and then she could turn back up on her own. Without the sound, she can't do anything, not even log in.

Is there a way to force sound on, from login screen? Specifically, if someone mutes her computer and then forgets to unmute before turning it off. I need her computer to have sound from when the login screen is up, so she can login to her computer.

I will reply later today with the version of Ubuntu she has and we'll , I don't know what other information is needed.

---

### Post by TheFu on 2024-04-26
Audio is usually controlled on a per-login basis, so I don't know how to enable anything related to audio until after a GUI session is started - after login.  Just setting the volume to 50% or 75% at login should help tremendously (I'd guess).

**inxi -Fxz** will provide all the information needed (and more). May need to install that program.

Without the exact DE and Ubuntu version and sound subsystem spelled out, we can't provide the correct command that will set the volume after she logs in.  She could be using pulseaudio or pipewire or jack ... and I think they all have different terminal tools to manage volume.

---

