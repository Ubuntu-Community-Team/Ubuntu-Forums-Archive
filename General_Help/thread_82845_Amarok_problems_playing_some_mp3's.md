---
title: "Amarok problems playing some mp3's"
date: 2005-10-27
forum: General Help
---

### Post by ILikeLinux on 2005-10-27
AmaraK just stutters while playing some of the mp3 song, while other are playing OK. However, when I play those mp3's which commandline mpg321, they are playing fine. 

For amarok, I am using the input - gst-engine,  output - alsasink.

Thanks for any suggestions.

---

### Post by hogweed on 2005-10-27
Yeah, I am having the same problem. I upgraded to Amarok 1.3.5 from the Kubuntu site, am using the updated gstreamer, but still having problems. I have noticed that this is only with mp3s encoded below 128k, and that the problem gets worse the lower the encoding.

In what may be a seperate issue, I am also finding that my radio streams in Amarok are pretty hit and miss as far as actually functioning.

Any clues?

-- hogweed

---

### Post by uten on 2005-10-27
mine will play songs but will take long to transition to the next track, and while it is transitioning the gui freezes. u cant do anything to the window

---

### Post by beefsprocket on 2005-10-27
Does changing engines help? I use arts for most music because it doesn't skip on track changes -- I like the crossfade feature without a gap like gstreamer or xine create with the same feature. 

For lossless listening I'll switch to gstreamer but other than that, arts seems fine. Could also be the alsa gstreamer -- try gstreamer with any of the other engines and hear what happens.

---

### Post by uten on 2005-10-27
i am using arts, and gstreamer is worse

---

### Post by Breaks on 2005-10-27
Well xine + alsa work just fine for me, no issues with playing tracks and all my radio streams work peachily... try that combination?

---

### Post by Staesys on 2005-10-27
I get stutters on my computer when using gstreamer. Xine runs the best of all I've tried.

---

### Post by ILikeLinux on 2005-10-28
Thanks to everyone who replied. 

I have now installed the xine engine and using xine+alsa - seems to work better. Will be able to verify only after using it with more mp3's.

---

### Post by alvonsius on 2005-10-28
Just wanna share my experience. I'm using Xine + alsa, and when I activated the crossfading the equalizer goes to 0 (reset back to normal, plain on 0) everytime amarok go to the next song. Maybe you have the same problem, maybe you dont ... but now I dont use the crossfading effect.

---

### Post by thomax on 2005-10-28
Go to configure amarok > engine > gst-streamer with oss sink or arts sink, haven't tested the others but they work fine for me, be shure to have one of these arts, alsa, or OSS(open sound system) installed

---

### Post by starpause on 2005-12-23
the gstreamer engine in amaroK was skipping (it sounded like buffer under runs) for all bit rate mp3s with my maudio audiophile 2496.

i used synaptic package manager to grab the xine engine and after switching over to that things have been peachy keen. 

i've tried a bunch of players and amaroK is my favorite yet! i also joined the [amaroK users group @ last.fm]("http://www.last.fm/group/amaroK%2Busers") :cool:

---

