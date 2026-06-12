---
title: "Adding lightdm event sounds"
date: 2016-09-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-09-05
i have ubuntu-sounds installed
i wanted to add login/logout and login ready sound events to lightdm
i put commands in the session startup/cleanup and greeter setup scripts to play sounds
like this:
[FONT=courier new]ogg123 /usr/share/sounds/ubuntu/stereo/desktop-login.ogg[/FONT]
it does not work how to i make it so lighdm can play audio?
this is what happens
```
Audio Device:   PulseAudio Output

Playing: /usr/share/sounds/ubuntu/stereo/system-ready.ogg
Ogg Vorbis stream: 1 channel, 44100 Hz
Home directory not accessible: Permission denied
ERROR: Cannot open device pulse.
```

---

