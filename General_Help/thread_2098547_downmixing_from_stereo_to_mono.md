---
title: "downmixing from stereo to mono?"
date: 2012-12-26
forum: General Help
---

### Post by lightsaberlesbian on 2012-12-26
I have to listen to these annoying lectures recorded with output only in one ear.  I tried googling downmixing audio from stereo to mono for VLC and linux but I've come up dry.  Does anyone know how to do this without having to buy an adapter or pulling the headphone jack out haflway? (also how does this even work?)

---

### Post by Dennis N on 2012-12-27
If the source is an mp3 file, its easy. Install lame, it is a command line encoder (found in repositories). It will mix down the stereo to mono.

Example: If song.mp3 is on the Desktop,

```
dan@Roxanne:~/Desktop$ lame --mp3input song.mp3 -m m -b 160 song_mono.mp3
```

See the man page for all the options for lame.

---

### Post by lightsaberlesbian on 2012-12-27
Unfortunately I'm dealing w/ ASF files  I may just have to deal with this inconvenience.  Good to know tho.  Thanks

---

