---
title: "Midi"
date: 2005-05-07
forum: General Help
---

### Post by fractalvibes on 2005-05-07
Getting MIDI playback seems the biggest stumbling block to my Linux installation...cannot get JACK to work,  ALSA keeps failing when it is initiated from various app.  It should not have to be this difficult.  I think MIDI files are playing, it is just the routing of that to the soundcard.  I actually have a Roland Sound Canvas hooked up via the joystick port on the back of the cheapo sound card.

I realize the cheapo soundcard has no onboard support ( a midisynth).  
When I do pmidi -l it shows:

Port		client name		port name
64:0		ES1370		                 ES1370

so maybe it does not differentiate between the card  and the external device?

Audio, such as CDs, mp3 play fine.  MIDI support seems something left out of Linux except for those who are fanatics that like fiddling with each little technical 
detail to get the simplest thing working....not for average Joe user for sure!

fv

---

### Post by fishfork on 2005-05-10
I had the same problem of MIDI not working with my cheap laptop soundcard. I managed to set up a software synth using Timidity after much trawling of the forum and I've expanded the [wiki page on software synthesis](https://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo). Let me know if it works for you (or doesn't).

Edit: just realised this is probably not what you're looking for. I'm not sure about external MIDI, sorry.

---

