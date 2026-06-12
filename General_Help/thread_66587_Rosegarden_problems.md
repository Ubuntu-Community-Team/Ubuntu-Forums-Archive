---
title: "Rosegarden problems"
date: 2005-09-17
forum: General Help
---

### Post by trondhl on 2005-09-17
I have tried for several days to get Rosegarden to work. In the config it says "Midi ok, audio ok" but when I try to play a midi file there is no sound. I get sound when I play the same file from the terminal using TiMidity.

I get the following error message in tty1: "ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave". I don't know if ALSA is configured properly, but i get the test sound running on the Multimedia Systems Selector.

Anyone who know what could be wrong?

---

### Post by Number6 on 2005-09-23
Yeah I've been struggling with rosegarden for a while too, with all the great help in these forums I've got to the stage where I have a soundfont loaded, jackd is happy (finally!), modules loaded etc "MIDI OK, Audio OK" in the sequencer config, but when I play a midi song (such as The Rosegarden from the examples!) It plays the first note of each track and then silence, until I stop and then restart (pause) the song, and then I get one note again then silence!

Just a note I did install Timidity, but as I understand it I dont actually need it becuase I have an SB Live!

---

