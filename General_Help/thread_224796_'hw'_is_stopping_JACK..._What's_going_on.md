---
title: "'hw' is stopping JACK... What's going on?"
date: 2006-07-28
forum: General Help
---

### Post by Silver Streak on 2006-07-28
Long story, but I'm trying to initialize JACK using the following command:

```
jackd -d alsa -d hw -r 44100 -p 2048 -n 2
```

However, it doesn't start; it outputs this:

```
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw|hw|2048|2|44100|0|0|nomon|swmeter|-|32bit
the playback device "hw" is already in use. Please stop the application using it  and run JACK again
cannot load driver module alsa
no message buffer overruns

```

Does anyone know what this 'hw' thing is, and why it's preventing JACK from starting?

SS

---

### Post by hanzomon4 on 2006-07-29
It means that some othe program is using the soundcard You may need to edit or create a file located in /etc/asound.conf to add the demix option. This allows more then I program to use the soundcard.

Do a search with the name of your soundcard to find out what you need to set up dmix in the asound.conf for your soundcard

If you post the name of your soundcard I may be able to help you find the proper instructions for setting up your asound.conf

---

