---
title: "Audacity not able to play while RhythmBox is ... But Totem happy to oblige"
date: 2007-06-18
forum: General Help
---

### Post by Geekkit on 2007-06-18
Sorry for the long title but that's in essence what I noticed. I was wondering if anyone knows if there is some sort of configuration twiddling one can do to satisfy Audacity so that it can play sounds while another application is playing a sound.

So, RhythmBox plays streaming music, and if I tell Audacity to open a WAV file and play it gives me the following error:

[INDENT]Error while opening sound device. Please check the output device settings and the project sample rate.[/INDENT]

Now if I open up that same WAV file Totem, Totem obliges just fine and plays the sound. If I close RhythmBox, then Audacity can play the sounds. I know someone's going to slap me for this and simply say "Stop playing RhythmBox so that Audacity can run you twit!" but I figure if one application can do it (i.e., Totem), then Audacity should be able to too. Anyone have any idea?

Thanks in advance if you have time.

:p

---

### Post by tgoose on 2007-06-18
I may be wrong, but I think that Rhythmbox and Totem both use Gstreamer, so they're happy to work together. Audacity, on the other hand, doesn't and also hasn't been updated for quite some time. If you run a programme called JACK by downloading qjackctl from synaptic, then this should allow you to run multiple streams without them even realising, but I couldn't be sure.

---

