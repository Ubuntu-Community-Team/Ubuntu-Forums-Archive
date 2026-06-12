---
title: "sound capture problem"
date: 2008-04-23
forum: General Help
---

### Post by Dave Otter on 2008-04-23
No sound capture in Hardy
     Have checked alsa mixer,volume control etc...
              Any ideas before I revert to Gutsy

---

### Post by ryanhaigh on 2008-04-24
What are you using to record? I have never had a lot of success with gnome-sound-recorder so use arecord from the terminal instead. Post the output of ```
arecord -l
``` which will list your devices. Then we can use something like ```
arecord -D plughw:0,0 -d 60 output.wav
``` to do the recording.

---

### Post by jhnphm on 2008-04-25
gnome-sound-recorder actually works now that pulseaudio is the default sound system.

---

