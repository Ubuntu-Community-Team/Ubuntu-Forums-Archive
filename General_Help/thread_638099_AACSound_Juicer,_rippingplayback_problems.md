---
title: "AAC/Sound Juicer, ripping/playback problems?"
date: 2007-12-11
forum: General Help
---

### Post by Syg on 2007-12-11
I am having problems ripping to AAC using Sound Juicer. The process seems to go fine, but when I try to play them (in any player - Totem, Songbird, etc.) the time increases dramatically (2.48 song becomes 11.25) and they only play in short bursts. I have also tried putting the songs on my ipod, but they still do not play (they are skipped entirely, although it's possible to see that the time increase remains).

I've also tried ripping to MP3 before: I've tried at least 4 times to get Sound Juicer to rip MP3s, but it just doesn't seem to work. AAC does seem more promising though.

I would stick with the Ogg format, but Apple doesn't really seem into the whole 'free as in freedom' thing and they won't play on my ipod.

Any help will be appreciated!

(Sorry if this is an easy fix: I'm a bit of a Linux newb, and Windows has corrupted my mind!)

Running Ubuntu 7.10 x86_64

---

### Post by Syg on 2007-12-12
Bump...

---

### Post by danwood76 on 2007-12-12
This may sound a little silly.

But have you installed the codec correctly from synaptic/apt ?
the codec is called faac, also for mp3 you will need the lame codec, with these installed correctly you should have no problems ripping.

I did once have problems ripping on another PC running feisty, to fix it I deleted all of the gnome sound profiles and re-created them manually.
For some reason sound juicer wasnt able to see the whole list of codecs available until I remade them,

hope it helps,
Danny

---

### Post by danwood76 on 2007-12-12
on a side note the aac codec is included in the gstreamer ugly-plugins pack which is also in the ubuntu repositry.
Installing this may help you.

regards,
Danny

---

### Post by Syg on 2007-12-15
I made sure the packages were installed, then I tried ripping again with no luck. Same problems as before.

Perhaps I could rip in another format, say Ogg or Flac, and then convert it to AAC or MP3? Is there a way I could do this instead?

---

### Post by reader4 on 2008-02-27
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/95326](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/95326)

---

