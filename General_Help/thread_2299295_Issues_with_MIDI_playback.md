---
title: "Issues with MIDI playback?"
date: 2015-10-17
forum: General Help
---

### Post by ilprodebasler on 2015-10-17
So, just yesterday I could easily use this website with Firefox: onlinesequencer.net
Now, however, it does not make a sound, and is therefore unusable.

I think this could be an issue related to MIDI playback in general, because when I use Audacious to play a MIDI file it's very sloppy (stops working all of a sudden, starts playing too late etc.), and this too is a problem that just popped up today all of a sudden.
What do you think I should try to do? 

I'm pretty sure Audacious uses ALSA and Timidity to play .mid files, but I don't know what Firefox uses. Also I'm using Lubuntu.

Thank you in advance for your help and attention.

---

### Post by mcduck on 2015-10-17
Firefox doesn't have any built-in midi player. Any audio you'd expect to hear at onlinesequencer.net would be the web site itself playing back the MIDI data into audio. Seems to be based on Javascript and OGG audio files so it *should* work fine on Firefox, assuming your web connection is fast enough to stream the audio back to you.

---

