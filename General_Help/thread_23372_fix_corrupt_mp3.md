---
title: "fix corrupt mp3?"
date: 2005-04-01
forum: General Help
---

### Post by taygan on 2005-04-01
hmmm.. I've got an mp3, 256kbit/s 44100 Hz, MPEG I layer III, 

trying to convert to .wav

but mpg123 reads it as 

Junk at the beginning 49443303
MPEG 2.0 layer III, 24 kbit/s, 22050 Hz joint-stereo
Warning, flexibel rate not heavily tested!
big_values too large!
mpg123: Can't rewind stream by 1127 bits!
Illegal Audio-MPEG-Header 0x1fc0e9fa at offset 0xa43.

I've tried "mpg123 --rate 44100 --stereo --resync" with no luck.

lame proceeds to decode it at half speed with lots of rate errors.

xmms will read it fine.

I've not had this problem before.  Any ideas?

---

