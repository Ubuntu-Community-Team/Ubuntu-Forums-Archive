---
title: "[SOLVED] Teamspeak with pulseaudio help please (have tried everything)"
date: 2008-06-13
forum: General Help
---

### Post by Gizmo89 on 2008-06-13
hi everyone

i was recently able launch teamspeak with pulseaudio, with headphones and mic all working, but for some reason the mic isn't anymore :s
i've seen posts on this forum and have tried people's posted solutions, but they have all failed for me.

can anyone help?

note: typing in padsp teamspeak (successfully opening the program), mutes the mic some how :S

---

### Post by Gizmo89 on 2008-06-13
forgot to mention that after it worked, i got my updates window come up with the usual packadges.
could it be possible for one of the updates to miss up the mic sound?
particularly "gstreamer 0.10"...

---

### Post by Gizmo89 on 2008-06-13
lol think i've fixed it, (For now, but if it goes wrong i will have to post :/ *cries like a baby*)

looked in /etc/pulse/daemon.conf and i changed it wrong :(
this is what i changed to (wrong way;uncommented)
; default-sample-format = s16le
; default-sample-rate = 44100
 default-sample-channels = 5

and this is the correction (commented + 5 for my 5.1 surround)
; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 5

small difference, but what can i say, i'm bad with instructions?!
note: i shall being posting again if it goes wrong :| *sighs*

---

