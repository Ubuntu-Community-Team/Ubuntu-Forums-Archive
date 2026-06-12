---
title: "JACK, alsa and emu10k1"
date: 2005-06-30
forum: General Help
---

### Post by DiesIrae on 2005-06-30
Hi there!
I've been trying to connect my guitar to my computer and make some recordings with Ardour.
Anyway, after installing jack and everything else it's not working, surprise surprise! :)

Well actually, everything "seems" to be working but I don't get any sound.
Here we go for the details:
I can start jackd with either the dummy driver or the alsa driver (with a few parameters to make alsa work). 
So far so good.

Now if I try to use Hydrogen directly with alsa everything works perfectly, but if I choose Jack in the options then I don't have any sound, even though hydrogen is connected to the alsa_pcm (or dummy_pcm) output.

If I try to redirect Hydrogen output to Ardour's input everything seems to be working: I can record it, and according to the nice display there IS some sound being processed somewhere, it's just that I can't hear it!

Finally I connect my guitar to the line in of my audio card I can hear it and record the sound through the gnome-sound-recorder, however if I try to record it with ardour, or to use some effects programs such as jack-rack or creox no sound seems to be processed.

I checked with alsamixer and none of the sliders are "muted", even though I have no idea what most of them are supposed to be anyway.

So I you had the same kind of problem before, or if you have any idea that might work...

Thanks,
Mathias

---

### Post by titanik837 on 2006-08-23
:) i have the same problem with the guitar but anyway do you understand this: 
jackrec -f filename [ -d second ] [ -b bitdepth ] [ -B bufsize ] port1 [ port2 ... ]

---

